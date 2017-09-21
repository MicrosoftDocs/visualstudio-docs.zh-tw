---
title: "擴充的方案總管篩選器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "方案總管] 中，擴充"
  - "擴充性 [Visual Studio]、 專案和方案"
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 擴充的方案總管篩選器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以擴充 **方案總管\] 中** 篩選功能套用到顯示或隱藏不同的檔案。 例如，您可以建立篩選，來顯示只有 C\# 類別處理站的檔案 **方案總管\] 中**, ，如本逐步解說示範。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### 建立 Visual Studio Package 專案  
  
1.  建立 VSIX 專案，名為 `FileFilter`。 新增自訂命令項目範本名為 **FileFilter**。 如需詳細資訊，請參閱[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  將參考加入 `System.ComponentModel.Composition` 和 `Microsoft.VisualStudio.Utilities`。  
  
3.  使上出現的功能表命令 **方案總管\] 中** 工具列。 開啟 FileFilterPackage.vsct 檔案。  
  
4.  變更 `<Button>` 區塊如下︰  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### 更新資訊清單檔  
  
1.  在 source.extension.vsixmanifest 檔案中，加入 MEF 元件的資產。  
  
2.  在 **資產** 索引標籤上，選擇 \[ **新增** \] 按鈕。  
  
3.  在 **類型** 欄位中，選擇 **Microsoft.VisualStudio.MefComponent**。  
  
4.  在 **來源** 欄位中，選擇 **目前方案中的專案**。  
  
5.  在 **專案** 欄位中，選擇 **FileFilter**, ，然後選擇 \[ **確定** 按鈕。  
  
### 新增篩選器程式碼  
  
1.  FileFilterPackageGuids.cs 檔案中加入一些 Guid:  
  
    ```c#  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  將類別檔案加入至名為 FileNameFilter.cs 的取值專案。  
  
3.  下列程式碼來取代空的命名空間和空的類別。  
  
     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` 方法會接受集合，其中包含方案的根目錄 \(`rootItems`\)，並傳回包含在篩選中的項目集合。  
  
     `ShouldIncludeInFilter` 方法篩選中的項目 **方案總管\] 中** 您指定的條件在階層。  
  
    ```c#  
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
  
4.  在 FileFilter.cs，移除取值建構函式中的命令位置和處理程式碼。 結果應該如下所示︰  
  
    ```c#  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     移除的 ShowMessageBox\(\) 方法。  
  
5.  在 FileFilterPackage、 cs、 取代 initialize （） 方法中的程式碼取代為下列︰  
  
    ```c#  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### 測試您的程式碼  
  
1.  建置並執行專案。 Visual Studio 的第二個執行個體隨即出現。 這稱為實驗執行個體。  
  
2.  在 Visual Studio 的實驗執行個體，開啟 C\# 專案。  
  
3.  尋找您在 \[方案總管\] 工具列新增\] 按鈕。 它應該是從左邊的第四個按鈕。  
  
4.  當您按一下按鈕時，所有檔案應該都篩選掉，以及您應該會看到 「 所有項目已都篩選檢視中。 」 在 \[方案總管\] 中。