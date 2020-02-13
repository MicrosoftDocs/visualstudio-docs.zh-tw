---
title: 將資料儲存在專案檔中 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30d6652480318898e1528a6f2bb61b84621636d6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848745"
---
# <a name="save-data-in-project-files"></a>將資料儲存在專案檔中
專案子類型可以儲存和抓取專案檔中的子類型特定資料。 Managed Package Framework （MPF）提供兩個介面來完成這項工作：

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 介面允許從專案檔的**MSBuild**區段存取屬性值。 當使用者需要載入或儲存組建相關資料時，任何使用者都可以呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 所提供的方法。

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 用來以自由格式的 XML 保存非組建相關資料。 每當 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 需要在專案檔中保存非組建相關的資料時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 就會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 所提供的方法。

  如需如何保存組建和非組建相關資料的詳細資訊，請參閱[將資料保存在 MSBuild 專案檔中](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)。

## <a name="save-and-retrieve-build-related-data"></a>儲存並抓取組建相關資料

### <a name="to-save-a-build-related-data-in-the-project-file"></a>將組建相關的資料儲存在專案檔中

- 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 方法，以儲存專案檔的完整路徑。

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string newFullPath = GetNewFullPath();
    // Set a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));
    ```

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>若要從專案檔中取出組建相關資料

- 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> 方法，以取得專案檔的完整路徑。

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string fullPath;
    // Get a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));
    ```

## <a name="save-and-retrieve-non-build-related-data"></a>儲存並取出非組建相關資料

### <a name="to-save-non-build-related-data-in-the-project-file"></a>若要在專案檔中儲存非組建相關資料

1. 執行 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> 方法，以判斷 XML 片段在上次儲存至其目前檔案之後是否已變更。

    ```
    public int IsFragmentDirty(uint storage, out int pfDirty)
    {
        pfDirty = 0;
        switch (storage)
        {
            case (uint)_PersistStorageType.PST_PROJECT_FILE:
            {
                if (isDirty)
                    pfDirty |= 1;
                break;
            }
            case (uint)_PersistStorageType.PST_USER_FILE:
            {
                // We do not store anything in the user file.
                break;
            }
        }

        // Forward the call to inner flavor(s)
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);

        return VSConstants.S_OK;

    }
    ```

2. 執行 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> 方法，將 XML 資料儲存在專案檔中。

    ```
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)
    {
        pbstrXMLFragment = null;

        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Create XML for our data.
                    XmlDocument doc = new XmlDocument();
                    XmlNode root = doc.CreateElement(this.GetType().Name);

                    XmlNode node = doc.CreateElement(targetsTag);
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));
                    root.AppendChild(node);

                    node = doc.CreateElement(updateTargetsTag);
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));
                    root.AppendChild(node);

                    doc.AppendChild(root);
                    // Get XML fragment representing our data
                    pbstrXMLFragment = doc.InnerXml;

                    if (fClearDirty != 0)
                        isDirty = false;
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);

        return VSConstants.S_OK;
    }
    ```

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>若要在專案檔中取出非組建相關資料

1. 執行 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> 方法，以初始化專案延伸模組屬性和其他與組建無關的資料。 如果專案檔中沒有 XML 設定資料，則會呼叫這個方法。

    ```
    public int InitNew(ref Guid guidFlavor, uint storage)
    {
        //Return,if it is our guid.
        if (IsMyFlavorGuid(ref guidFlavor))
            return VSConstants.S_OK;

        //Forward the call to inner flavor(s).
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);

        return VSConstants.S_OK;
    ```

2. 執行 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> 方法，從專案檔載入 XML 資料。

    ```
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)
    {
        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Load our data from the XML fragment.
                    XmlDocument doc = new XmlDocument();
                    XmlNode node = doc.CreateElement(this.GetType().Name);
                    node.InnerXml = pszXMLFragment;
                    if (node == null
                        || node.FirstChild == null
                        || node.FirstChild.ChildNodes.Count == 0
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)
                        break;
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;

                    if (node.FirstChild.ChildNodes.Count <= 1
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)
                        break;
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);

        return VSConstants.S_OK;
    }
    ```

> [!NOTE]
> 本主題中提供的所有程式碼範例都是[VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)中較大範例的一部分。

## <a name="see-also"></a>請參閱
- [將資料保存在 MSBuild 專案檔中](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
