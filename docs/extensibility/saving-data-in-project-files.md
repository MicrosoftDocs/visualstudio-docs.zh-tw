---
title: 在項目檔中儲存資料 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fd6cfaa450bc268665ae0f58109c99002da6152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701347"
---
# <a name="save-data-in-project-files"></a>儲存資料檔案
專案子類型可以在專案檔中保存和檢索特定於子類型的數據。 託管套件框架 (MPF) 提供兩個介面來完成此工作:

- 該<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>介面允許從專案檔的**MSBuild**部分訪問屬性值。 只要使用者需要載入<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>或保存生成相關數據,任何使用者都可以調用所提供的方法。

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>用於在自由格式 XML 中保留非生成相關數據。 只要需要在專案檔中<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>保留非生成相關數據,就會調用提供的方法[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)][!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。

  有關如何保留生成和非產生相關資料的詳細資訊,請參閱[MSBuild 專案檔中的持久資料](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)。

## <a name="save-and-retrieve-build-related-data"></a>儲存和檢索產生相關資料

### <a name="to-save-a-build-related-data-in-the-project-file"></a>在專案檔案中儲存與產生相關資料

- 調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>方法以保存專案檔的完整路徑。

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

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>從專案檔案中檢索產生相關資料

- 調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A>方法以檢索專案檔的完整路徑。

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

## <a name="save-and-retrieve-non-build-related-data"></a>儲存及檢索非產生相關資料

### <a name="to-save-non-build-related-data-in-the-project-file"></a>在專案檔案中儲存非產生相關資料

1. 實現該方法<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A>以確定自上次保存到其當前文件以來 XML 片段是否已更改。

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

2. 實現在<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>專案檔中保存 XML 資料的方法。

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

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>在專案檔案中檢索非產生相關資料

1. 實現初始<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A>化專案擴展屬性和其他與生成無關的數據的方法。 如果專案檔中不存在 XML 設定數據,則呼叫此方法。

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

2. 實現從<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>專案檔載入 XML 資料的方法。

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
> 本主題提供的所有代碼示例都是[VSSDK 範例中](https://github.com/Microsoft/VSSDK-Extensibility-Samples)較大範例的一部分。

## <a name="see-also"></a>另請參閱
- [MSBuild 專案檔中的持久資料](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
