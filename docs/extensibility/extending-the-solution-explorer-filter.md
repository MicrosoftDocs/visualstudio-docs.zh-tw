---
title: 延伸解決方案資源管理員篩選器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af0824edd4188481bec8c0703d71043354f5dbcc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711564"
---
# <a name="extend-the-solution-explorer-filter"></a>擴充解決方案資源管理員篩選器
您可以擴充**解決方案資源管理員**篩選器功能以顯示或隱藏不同的檔案。 例如,您可以創建一個篩選器,該篩選器在**解決方案資源管理器**中僅顯示 C# 類工廠檔,正如本演練所示。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="create-a-visual-studio-package-project"></a>建立視覺化工作室套件專案

1. 創建名為的`FileFilter`VSIX 專案。 添加名為**FileFilter 的**自定義命令項範本。 關於詳細資訊,請參閱[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

2. 添加對`System.ComponentModel.Composition`和`Microsoft.VisualStudio.Utilities`的引用。

3. 使功能表命令顯示在**解決方案資源管理員**工具列上。 開啟*檔案篩選器套件.vsct*檔案。

4. 將`<Button>`區塊變更為以下內容:

    ```xml
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>FileNameFilter</ButtonText>
        </Strings>
    </Button>
    ```

### <a name="update-the-manifest-file"></a>更新資訊清單檔

1. 在*source.擴展.vsixmanifest 檔中*,添加作為 MEF 元件的資產。

2. 在「**資產**」選項卡上,選擇「**新建」** 按鈕。

3. 在 **「類型」** 欄位中,選擇**Microsoft.VisualStudio.Mef 元件**。

4. 在 **「來源」** 欄位中,選擇**目前解決方案中的項目**。

5. 在 **「專案」** 欄位中,選擇 **「檔案篩選器**」,然後選擇「**確定**」 按鈕。

### <a name="add-the-filter-code"></a>新增篩選器代碼

1. 從*FileFilterPackageGuids.cs*檔案加入 GUID:

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. 將類檔添加到名為*FileNameFilter.cs*的檔案篩選器專案。

3. 將空命名空間和空類替換為下面的代碼。

     該方法`Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)`採用包含解決方案`rootItems`( ) 根的集合,並返回要包含在篩選器中的項的集合。

     該方法`ShouldIncludeInFilter`根據指定的條件篩選**解決方案資源管理器**層次結構中的項。

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

4. 在*FileFilter.cs*中,從 FileFilter 建構函數中刪除命令放置和處理代碼。 結果應如下所示:

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

     也刪除`ShowMessageBox()`方法。

5. 在*FileFilterPackage.cs*中,將`Initialize()`方法中 的代碼取代為以下內容:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>測試您的程式碼

1. 建置並執行專案。 Visual Studio 的第二個執行個體隨即出現。 這稱為實驗實例。

2. 在 Visual Studio 的實驗中,打開 C# 專案。

3. 尋找在**解決方案資源管理員**工具列上添加的按鈕。 它應該是左側的第四個按鈕。

4. 按下該按鈕時,應篩選出所有文件,並且應看到**所有專案都已從視圖中篩選出來。** 在**解決方案資源管理員**中。
