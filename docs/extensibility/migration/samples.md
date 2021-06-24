---
title: 更新 Visual Studio 延伸模組的 ImageOptimizer 範例
description: 遵循範例以瞭解如何更新 Visual Studio 延伸模組，以使用 Visual Studio 2022 Preview。
ms.date: 06/08/2021
ms.topic: sample
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 12bbc159884c16ea89849e5c97a4b87292f7089d
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602225"
---
# <a name="imageoptimizer---update-a-visual-studio-extension-step-by-step"></a>ImageOptimizer-逐步更新 Visual Studio 擴充功能

[!INCLUDE [preview-note](../includes/preview-note.md)]

本指南將說明新增 Visual Studio 2022 支援所需的所有步驟，同時保有使用影像優化程式擴充功能的 Visual Studio 2019 支援作為個案研究。  
這是每個步驟的 git 認可連結的完整指南，但您可以在這裡看到已完成的 PR： [https://github.com/madskristensen/ImageOptimizer/pull/46](https://github.com/madskristensen/ImageOptimizer/pull/46) 。

本指南的結尾也有 [其他範例](#other-samples) 。

## <a name="step-1---modernize-the-project"></a>步驟 1-將專案現代化

請參閱 [將專案現代化](update-visual-studio-extension.md#modernize-your-vsix-project)。

[git 認可 e052465](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e052465f30e6bed37e6d76eac016047095e8e18b)

首先我們會將 VSIX 和單元測試專案，在專案的 [屬性] 頁面下，將 [VSIX] 和 [單元測試] 專案

   ![Framework 版本的凸塊](media/samples/framework-bump.png)

影像優化器參考一些舊的自訂 14. * 和 15. * 套件，而是會安裝[ `Microsoft.VisualStudio.Sdk` NuGet 套件](https://www.nuget.org/packages/microsoft.visualstudio.sdk)，以合併我們所有的必要參考。

```Diff
-  <ItemGroup>
-    <PackageReference Include="Madskristensen.VisualStudio.SDK">
-      <Version>14.0.0-beta4</Version>
-    </PackageReference>
-    <PackageReference Include="Microsoft.VSSDK.BuildTools">
-      <Version>15.8.3247</Version>
-      <IncludeAssets>runtime; build; native; contentfiles; analyzers</IncludeAssets>
-      <PrivateAssets>all</PrivateAssets>
-    </PackageReference>
-  </ItemGroup>

+  <ItemGroup>
+    <PackageReference Include="Microsoft.VisualStudio.SDK">
+      <Version>16.9.31025.194</Version>
+    </PackageReference>
+  </ItemGroup>
```

建立專案成功，我們會收到一些執行緒警告。 修正這些警告的方法是按一下 `ctrl` 和 `.` ，並使用 intellisense 來新增遺漏的執行緒切換線。

## <a name="step-2---refactor-source-code-into-a-shared-project"></a>步驟 2-將原始程式碼重構為共用專案

請參閱 [共用的專案](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting)。

支援 Visual Studio 2022 需要加入新的共用專案，其中將包含延伸模組的原始程式碼，該程式碼將在 Visual Studio 2019 和 Visual Studio 2022 VSIX 專案之間共用。

1. 將新的共用專案加入至您的方案

   [git 認可 abf249d](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/abf249d5a4bed9010652f3f3fc4753c7c771c892)

   ![新增共用的專案](media/samples/add-shared-project.png)

1. 將共用專案的參考加入至您的 VSIX 專案。

   [git 認可 e8e941e](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e8e941e5a5482cc15f5b9e7e4f1727f5cab5b12c)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="新增共用的專案參考" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. 將您的原始程式碼檔 (cs、xaml、resx) 移至新的共用專案，但下列專案 **除外** ：
    - `source.extension.vsixmanifest`
    - 擴充元資料檔案 (圖示、授權、版本資訊等 ) 
    - .VSCT 檔案
    - 連結的檔案
    - 需要包含在 VSIX 中的外部工具或程式庫

   [git 認可 f31f051](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/f31f0515305623988f2c355ed3bf5952fc8f1d9e)

   ![將檔案移至共用的專案](media/samples/move-to-shared-project.png)

1. 現在將所有中繼資料、.VSCT 檔、連結的檔案和外部工具/程式庫移至共用位置，然後將其新增回 VSIX 專案的連結專案。 **請勿** 移除 `source.extension.vsixmanifest` 。

   [git 認可 73ba920-移動檔案](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/73ba920b7db0bdb7c4d66aa9bc932c268efd49cb)

   [git 認可 d5e36b2-新增外部工具/程式庫](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d5e36b2d047290d38ffc977511510bc03e257f13)

   1. 針對此專案，我們必須將延伸模組圖示、.VSCT 檔和外部工具移至新的資料夾 `ImageOptimizer\Resources` 。 將它們複製到共用資料夾，並將它們從 VSIX 專案中移除。
   1. 將它們新增回連結的專案，而且如果專案已經連結的專案，就可以保持 (授權範例) 。
   1. 藉由選取每一個，並檢查 [屬性] 工具視窗，確認已新增連結的檔案中已正確設定組建動作和其他屬性。 針對我們的專案，我們必須設定下列專案：
       - 將 `icon.png` 組建動作設定為 `Content` ，並將包含在 VSIX 中標記為 `true`
       - 將 `ImageOptimizer.vsct` 組建動作設定為 `VSCTComplile` ，並將其包含在 VSIX 中 `false`
       - 將 [ `Resources\Tools` `Content` 包含在 VSIX 中的檔案] 的所有組建動作設定為 `true`

           ![將連結的檔案新增至 VSIX 專案](media/samples/add-linked-files.png)

       - 此外， `ImageOptimizer.cs` 是的相依性 `ImageOptimizer.vsct` ，我們必須手動將此相依性新增至 .csproj 檔案：

          ```diff  
          - <Content Include="..\SharedFiles\ImageOptimizer.vsct">
          -   <Link>ImageOptimizer.vsct</Link>
          - </Content>
          - <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          -   <Link>ImageOptimizer.cs</Link>
          - </Compile>

          + <VSCTCompile Include="..\SharedFiles\ImageOptimizer.vsct">
          +   <ResourceName>Menus.ctmenu</ResourceName>
          +   <Generator>VsctGenerator</Generator>
          +   <LastGenOutput>..\SharedFiles\ImageOptimizer.cs</LastGenOutput>
          + </VSCTCompile>
          + <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          +   <AutoGen>True</AutoGen>
          +   <DesignTime>True</DesignTime>
          +   <DependentUpon>..\SharedFiles\ImageOptimizer.vsct</DependentUpon>
          + </Compile>
          ```

       - 如果 [屬性] 工具視窗防止您設定特定的組建動作，您可以手動修改上述的 .csproj，然後視需要設定組建動作。

1. 建立您的專案以驗證您的變更，並修正任何錯誤/問題。 請參閱 [常見問題](update-visual-studio-extension.md#q--a) 一節，以瞭解常見的問題。

## <a name="step-3---add-a-visual-studio-2022-vsix-project"></a>步驟 3-新增 Visual Studio 2022 VSIX 專案

請參閱 [新增 Visual Studio 2022 目標](update-visual-studio-extension.md#add-a-visual-studio-2022-target)。

1. 將新的 VSIX 專案加入至方案。
1. 移除新專案中的任何其他原始程式碼，除了 `source.extension.vsixmanifest.`

   ![建立新的 VSIX 專案](media/samples/visual-studio-2022-vsix-initial.png)

1. 加入共用專案的參考。

   [git 認可 dd49cb2](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/dd49cb227b52c46206bf4be5c25790ac0377568d)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="加入共用專案的參考" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. 從您的 Visual Studio 2019 VSIX 專案新增連結的檔案，並驗證其 "Build Action" 和 "Include in VSIX" 屬性相符。 也請複製您的檔案 `source.extension.vsixmanifest` ，稍後我們將會加以修改，以支援 Visual Studio 2022。

   [git 認可98c43ee](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/98c43ee6fbe912c38a1275542c44c65e11d7dbd9)

   ![將連結的檔案新增至 VSIX 專案](media/samples/visual-studio-2022-add-linked-files.png)

1. 嘗試的組建顯示我們遺漏了的參考 `System.Windows.Forms` 。 只要將它新增至我們的 Visual Studio 2022 專案並重建。

   [git 認可 de71ccd](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/de71ccd9baff703aa6679392ad41a2cfe7bd7d72)

   ```Diff
   + <Reference Include="System.Windows.Forms" />
   ```

1. 升級 `Microsoft.VisualStudio.SDK` 和 `Microsoft.VSSDK.BuildTools` 封裝 Visual Studio 2022 版本的參考。

   [git 認可 d581fc3](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d581fc3c954974124dc7e31e5ecc85f78f7828ab)

   > [!NOTE]
   > 這些是建立本指南時可用的最新版本。 建議您取得可用的最新版本。
   >
   > ```diff
   > -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
   > +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview-1-31216-1036" />
   > -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
   > +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-Visual Studio 2022-g3f11f5ab" />
   > ```

1. 編輯您的檔案 `source.extension.vsixmanifest` ，以反映 Visual Studio 2022 的目標。

   [git 認可9d393c7](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/9d393c708c04ac4af48d1eb9ce3da4470db5d5cc)
   1. 設定 `<InstallationTarget>` 標記以反映 Visual Studio 2022，並指出 amd64 承載：

      ```xml
      <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
          <ProductArchitecture>amd64</ProductArchitecture>
      </InstallationTarget>
      ```

   1. 修改必要條件以僅包含 Visual Studio 2022 和更新版本：

      ```Diff
      - <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,)" DisplayName="Visual Studio core editor" />
      + <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,)" DisplayName="Visual Studio core editor" />
      ```

我們已經完成了！

如此一來，現在就會產生 Visual Studio 2019 和 Visual Studio 2022 VSIXes。

## <a name="other-samples"></a>其他範例

- [ProPower 工具](https://github.com/microsoft/VS-PPT/pull/244)
  - PeekF1
    - 允許透過所選類別/物件的說明資訊來查看網頁瀏覽器。
  - FixMixedTabs
    - 掃描您的檔，並以空格取代定位字元，反之亦然

## <a name="next-steps"></a>後續步驟

請閱讀這份 [「開始至完成」指南](update-visual-studio-extension.md)，準備更新您的延伸模組。
