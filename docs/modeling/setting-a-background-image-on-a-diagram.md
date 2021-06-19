---
title: 設定圖表上的背景影像
description: 瞭解在 Visual Studio 的視覺效果和模型 SDK 中，您可以使用自訂程式碼來設定產生之設計工具的背景影像。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9304117932b92408f12a23747253de66dfd767d1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385665"
---
# <a name="setting-a-background-image-on-a-diagram"></a>設定圖表上的背景影像
在 Visual Studio 視覺效果和模型 SDK 中，您可以使用自訂程式碼，為產生的設計工具設定背景影像。

## <a name="setting-the-background-image"></a>設定背景影像

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>為產生的設計工具設定背景影像

1. 將您要用來做為圖表背景的影像檔複製到目前專案的 Dsl\Resources 目錄中。

2. 在 **方案總管** 中，以滑鼠右鍵按一下 [Dsl\Resources] 資料夾，指向 [ **加入**]，然後按一下 [ **現有專案**]。

3. 在 [ **加入現有專案** ] 對話方塊中，流覽至 [Dsl\Resources] 資料夾。

4. 在 [ **檔案類型** ] 清單中，按一下 [ **影像檔**]。

5. 按一下您複製到目錄的影像檔案，然後按一下 [ **新增**]。

6. **以滑鼠右鍵按一下 [** dsl]，然後按一下 [內容] 以開啟 dsl 專案的屬性。

7. 在 [ **資源** ] 索引標籤上，按一下 [ **此專案不包含預設資源檔]。按一下這裡以建立一個。**

8. 將影像從 **方案總管** 拖曳至資源視窗，以將影像檔新增至資源檔。

9. 開啟 [檔案] 功能表，然後按一下選項以儲存專案屬性。

10. 確認檔案 Dsl\Properties\Resources.resx 存在且其下有檔案 Resources.Designer.cs。

11. 如果缺少 .cs，請按一下 **方案總管** 中的檔案資源 .resx。

12. 在 [屬性]  視窗中，將 `Custom Tool` 屬性設定為 `ResXFileCodeGenerator`。

13. 在 **方案總管** 中，以滑鼠右鍵按一下 Dsl 專案，指向 [ **加入**]，然後按一下 [ **新增資料夾**]。

14. 將資料夾命名為 **Custom**。

15. 在 [自訂] 資料夾上按一下滑鼠右鍵，指向 [ **加入**]，然後按一下 [ **新增專案**]。

16. 在 [ **加入新專案** ] 對話方塊的 [ **範本** ] 清單中，按一下 [程式 **代碼** 檔案]。

17. 在 [ **名稱** ] 方塊中，輸入 `BackgroundImage.cs` ，然後按一下 [ **新增**]。

18. 將下列程式碼複製到 BackgroundImage.cs 檔，調整的命名空間、圖表類別名稱和影像檔資源名稱。

     將 "MyDiagramClass" 取代為 Dsl\GeneratedCode\Diagrams.cs 中所定義的圖表部分類別名稱。 您也可以從檔案 Dsl\GeneratedCode\Diagrams.cs 中擷取正確的命名空間。

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling.Diagrams;

    // Fix the namespace:
    namespace Fabrikam.MyLanguage
    {
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs

      public partial class Language29Diagram
      {
        protected override void InitializeInstanceResources()
        {
          // Fix the Resources namespace and the Image resource name:
          ImageField backgroundField = new ImageField("background",
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);

          backgroundField.DefaultFocusable = false;
          backgroundField.DefaultSelectable = false;
          backgroundField.DefaultVisibility = true;
          backgroundField.DefaultUnscaled = false;

          shapeFields.Add(backgroundField);

          backgroundField.AnchoringBehavior
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);
          backgroundField.AnchoringBehavior
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);
          backgroundField.AnchoringBehavior
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);
          backgroundField.AnchoringBehavior
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);

          base.InitializeInstanceResources();
        }
      }
    }
    ```

     如需使用程式碼自訂模型的詳細資訊，請參閱 [在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

## <a name="see-also"></a>另請參閱

- [定義圖案和連接器](../modeling/defining-shapes-and-connectors.md)
- [自訂文字和影像欄位](../modeling/customizing-text-and-image-fields.md)
- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
