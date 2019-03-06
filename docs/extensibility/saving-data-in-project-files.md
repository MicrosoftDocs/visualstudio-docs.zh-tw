---
title: 將資料儲存在專案檔 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6cd79925023a32a68ff4a9ac5f86f85d9c6798bf
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843590"
---
# <a name="save-data-in-project-files"></a>將資料儲存在專案檔
專案子類型可以儲存並擷取專案檔中的子型別特定資料。 Managed Package Framework (MPF) 提供兩個介面，以完成這項工作：

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>介面允許存取屬性值從**MSBuild**專案檔的區段。 所提供的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>可由任何使用者呼叫，只要載入或儲存使用者必須建立相關的資料。

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>用來保存自由格式的 XML 中的非建置相關的資料。 所提供的方法<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>會呼叫[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]每當[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]必須保存在專案檔中的非建置相關的資料。

  如需有關如何繼續進行建置和非建置相關的資料的詳細資訊，請參閱[將 MSBuild 專案檔中的資料保存](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)。

## <a name="save-and-retrieve-build-related-data"></a>儲存並擷取組建相關的資料

### <a name="to-save-a-build-related-data-in-the-project-file"></a>若要儲存組建相關的專案檔中的資料

-   呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>方法來儲存專案檔的完整路徑。

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

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>若要擷取組建從專案檔的相關資料

-   呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A>方法來擷取專案檔的完整路徑。

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

## <a name="save-and-retrieve-non-build-related-data"></a>儲存和擷取非建置相關的資料

### <a name="to-save-non-build-related-data-in-the-project-file"></a>若要儲存非建置相關的專案檔中的資料

1.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A>方法，以判斷是否已變更 XML 片段，自從上次儲存至其目前的檔案。

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

2.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>方法，將 XML 資料儲存在專案檔中。

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

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>若要擷取非建置相關的專案檔中的資料

1.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A>方法以初始化專案延伸模組屬性和其他組建無關的資料。 如果沒有出現在專案檔的 XML 組態資料，會呼叫這個方法。

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

2.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>從專案檔案載入 XML 資料的方法。

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
>  本主題所提供的所有程式碼範例會在較大範例的組件[VSSDK 範例](https://aka.ms/vs2015sdksamples)。

## <a name="see-also"></a>另請參閱
- [保存在 MSBuild 專案檔中的資料](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)