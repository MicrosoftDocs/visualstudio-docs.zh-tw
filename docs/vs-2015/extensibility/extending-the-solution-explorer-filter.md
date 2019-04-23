---
title: 擴充方案總管篩選 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 687663a79ea5dca75da68013519f4652fa71460c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110566"
---
# <a name="extending-the-solution-explorer-filter"></a>延伸方案總管篩選
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以延伸**方案總管 中**篩選功能，以顯示或隱藏不同的檔案。 例如，您可以建立篩選會顯示只有 C# 類別處理站中的檔案**方案總管 中**，如本逐步解說示範。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### <a name="create-a-visual-studio-package-project"></a>建立 Visual Studio Package 專案  
  
1. 建立 VSIX 專案，名為`FileFilter`。 新增名為的自訂命令項目範本**FileFilter**。 如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的擴充](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2. 將參考加入`System.ComponentModel.Composition`和`Microsoft.VisualStudio.Utilities`。  
  
3. 請在出現的功能表命令**方案總管 中**工具列。 開啟 FileFilterPackage.vsct 檔案。  
  
4. 變更`<Button>`區塊所示：  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### <a name="update-the-manifest-file"></a>更新資訊清單檔案  
  
1. 在 source.extension.vsixmanifest 檔案中，新增為 MEF 元件的資產。  
  
2. 在 [**資產**索引標籤上，選擇**新增**] 按鈕。  
  
3. 在 **型別**欄位中，選擇**Microsoft.VisualStudio.MefComponent**。  
  
4. 在 **來源**欄位中，選擇**目前方案中的專案**。  
  
5. 在 **專案**欄位中，選擇**FileFilter**，然後選擇**確定**按鈕。  
  
### <a name="add-the-filter-code"></a>新增篩選條件程式碼  
  
1. FileFilterPackageGuids.cs 檔案中加入一些 Guid:  
  
    ```csharp  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2. 將類別檔案新增至名為 FileNameFilter.cs FileFilter 專案中。  
  
3. 下列程式碼取代空的命名空間和空的類別。  
  
     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)`方法會採用包含在方案根目錄的集合 (`rootItems`)，並傳回包含在篩選條件的項目集合。  
  
     `ShouldIncludeInFilter`方法篩選中的項目**方案總管 中**根據您指定的階層。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Text.RegularExpressions;  
    using System.Threading.Tasks;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
  
    namespace FileFilter  
    {  
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component  
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]  
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider  
        {  
            SVsServiceProvider svcProvider;  
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
            // Constructor required for MEF composition  
            [ImportingConstructor]  
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)  
            {  
                this.svcProvider = serviceProvider;  
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
            }  
  
            // Returns an instance of Create filter class.  
            protected override HierarchyTreeFilter CreateFilter()  
            {  
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);  
            }  
  
            // Regex pattern for CSharp factory classes  
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";  
  
            // Implementation of file filtering  
            private sealed class FileNameFilter : HierarchyTreeFilter  
            {  
                private readonly Regex regexp;  
                private readonly IServiceProvider svcProvider;  
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
                public FileNameFilter(  
                    IServiceProvider serviceProvider,  
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,  
                    string fileNamePattern)  
                {  
                    this.svcProvider = serviceProvider;  
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);  
                }  
  
                // Gets the items to be included from this filter provider.   
                // rootItems is a collection that contains the root of your solution  
                // Returns a collection of items to be included as part of the filter  
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)  
                {  
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);  
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;  
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(  
                                        root.HierarchyIdentity.NestedHierarchy,  
                                        CancellationToken);  
  
                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(  
                        sourceItems,  
                        ShouldIncludeInFilter,  
                        CancellationToken);  
                    return includedItems;  
                }  
  
                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>  
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)  
                {  
                    if (hierarchyItem == null)  
                    {  
                        return false;  
                    }  
                    return this.regexp.IsMatch(hierarchyItem.Text);  
                }  
            }  
        }  
    }  
  
    ```  
  
4. 在 FileFilter.cs，移除 FileFilter 建構函式中的命令位置和處理程式碼。 結果應該如下所示：  
  
    ```csharp  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     移除的 ShowMessageBox() 方法。  
  
5. 在 FileFilterPackage、 cs、 將 initialize （） 方法中的程式碼取代為下列：  
  
    ```csharp  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### <a name="test-your-code"></a>測試您的程式碼  
  
1. 建置並執行專案。 Visual Studio 的第二個執行個體隨即出現。 這稱為實驗執行個體。  
  
2. 在 Visual Studio 的實驗性執行個體，開啟 C# 專案。  
  
3. 尋找您加入 [方案總管] 工具列的按鈕。 它應該是從左邊的第四個按鈕。  
  
4. 當您按一下按鈕時，所有檔案應該都篩選掉，以及您應該會看到 「 所有項目已都篩選檢視中。 」 在 [方案總管] 中。
