---
title: 擴充方案總管篩選準則 |Microsoft Docs
description: 瞭解如何延伸方案總管篩選功能，以顯示或隱藏 Visual Studio SDK 中的不同檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dfe2947d60ad5dde6e2f23b9bed59b09e6abe8ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862118"
---
# <a name="extend-the-solution-explorer-filter"></a>擴充方案總管篩選
您可以擴充 **方案總管** 篩選功能，以顯示或隱藏不同的檔案。 例如，您可以建立只在 **方案總管** 中顯示 c # class factory 檔案的篩選準則，如本逐步解說所示範。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

### <a name="create-a-visual-studio-package-project"></a>建立 Visual Studio 套件專案

1. 建立名為的 VSIX 專案 `FileFilter` 。 加入名為 **FileFilter** 的自訂命令專案範本。 如需詳細資訊，請參閱 [使用功能表命令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)模組。

2. 加入和的參考 `System.ComponentModel.Composition` `Microsoft.VisualStudio.Utilities` 。

3. 讓功能表命令出現在 **方案總管** 工具列上。 開啟 *FileFilterPackage .vsct* 檔案。

4. 將 `<Button>` 區塊變更為下列內容：

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

1. 在 *extension.vsixmanifest* 檔案中，新增屬於 MEF 元件的資產。

2. 在 [ **資產** ] 索引標籤上，選擇 [ **新增** ] 按鈕。

3. 在 [ **類型** ] 欄位中，選擇 [ **VisualStudio. [microsoft.visualstudio.mefcomponent]**]。

4. 在 [ **來源** ] 欄位中，選擇 [ **目前方案中的專案**]。

5. 在 [ **專案** ] 欄位中，選擇 [ **FileFilter**]，然後選擇 [ **確定]** 按鈕。

### <a name="add-the-filter-code"></a>新增篩選器程式碼

1. 將一些 Guid 新增至 *FileFilterPackageGuids.cs* 檔案：

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. 將類別檔案加入至名為 *FileNameFilter.cs* 的 FileFilter 專案。

3. 將空的命名空間和空白類別取代為下列程式碼。

     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)`方法會使用包含方案之根的集合 (`rootItems`) ，並傳回要包含在篩選中的專案集合。

     `ShouldIncludeInFilter`方法會根據您指定的條件，篩選 **方案總管** 階層中的專案。

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

4. 在 *FileFilter.cs* 中，從 FileFilter 的函式移除命令放置和處理常式代碼。 結果看起來應該像這樣：

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

     也請移除 `ShowMessageBox()` 方法。

5. 在 *FileFilterPackage.cs* 中，將方法中的程式碼取代為下列程式碼 `Initialize()` ：

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>測試您的程式碼

1. 建置並執行專案。 Visual Studio 的第二個執行個體隨即出現。 這稱為實驗實例。

2. 在 Visual Studio 的實驗實例中，開啟 c # 專案。

3. 尋找您在 **方案總管** 工具列上新增的按鈕。 它應該是左邊的第四個按鈕。

4. 當您按一下按鈕時，應該篩選出所有檔案，而且您應該會看到 **所有的專案都已從 view 篩選出來。** 在 **方案總管** 中。
