---
title: 產生 C# Equals 與 GetHashCode 方法的覆寫
description: 瞭解如何使用 [快速動作與重構] 功能表來產生 Equals 和 GetHashCode 方法。
ms.custom: SEO-VS-2020
ms.date: 03/08/2021
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 6a9d0ea6f6cb0aedc4fa13a8014b1a8bd66ccca0
ms.sourcegitcommit: 6ed6ae5a1693607dce57923a78d01eea3d88b29a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514936"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>在 Visual Studio 中產生 Equals 與 GetHashCode 方法覆寫

此程式碼產生適用於：

- C#

**功能：** 讓您產生 **Equals** 與 **GetHashCode** 方法。

**時機：** 當您有某個類型應由一或多個欄位比對，而不是由記憶體中的物件位置比對時，請產生這些覆寫。

**為什麼：**

- 如果您要執行實值型別，則應該考慮覆寫 **Equals** 方法。 當您這樣做時，您可以透過 ValueType 的 Equals 方法預設執行來提升效能。

- 如果您正在執行參考型別，則應該考慮覆寫 **Equals** 方法（如果您的型別看起來像是 Point、String、bignumber 等等等）。

- 覆寫 **GetHashCode** 方法以允許類型在雜湊表中正確運作。 如需更多指引，請參閱[等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)。

## <a name="how-to"></a>使用方法

1. 將游標放在型別宣告行的某個位置。

    ```csharp
    public class ImaginaryNumber
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }
    }
    ```

   您的程式碼看起來應該類似下列螢幕擷取畫面：

   ![醒目提示程式碼的螢幕擷取畫面，以套用產生的方法](media/overrides-highlight-cs.png)

   > [!TIP]
   > 請勿按兩下來選取型別名稱，否則功能表選項將無法使用。 只要將游標放在該行的某個位置即可。

1. 接下來，選擇下列其中一個動作：

   - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

   - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。

   - 按一下 ![Visual Studio 中快速動作螺絲起子圖示的螢幕擷取畫面](../media/screwdriver-icon.png) 圖示。

1. 從下拉式功能表選取 [產生 Equals(object)]或 [產生 Equals 和 GetHashCode]。

   ![[產生覆寫] 下拉式功能表的螢幕擷取畫面](media/overrides-preview-cs.png)

1. 在 [選取成員]對話方塊中，選取您想要產生方法的成員：

    ![[產生覆寫] 對話方塊](media/overrides-dialog-cs.png)

    > [!TIP]
    > 您也可以選擇使用對方塊底部附近的核取方塊，從此對話方塊中產生運算子。

   `Equals`和 `GetHashCode` 方法會使用預設的實值產生，如下列程式碼所示：

    ```csharp
   public class ImaginaryNumber : IEquatable<ImaginaryNumber>
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }

        public override bool Equals(object obj)
        {
            return Equals(obj as ImaginaryNumber);
        }

        public bool Equals(ImaginaryNumber other)
        {
            return other != null &&
                   RealNumber == other.RealNumber &&
                   ImaginaryUnit == other.ImaginaryUnit;
        }

        public override int GetHashCode()
        {
            return HashCode.Combine(RealNumber, ImaginaryUnit);
        }
    }
    ```

   您的程式碼看起來應該類似下列螢幕擷取畫面：

   ![所產生方法的結果螢幕擷取畫面](media/overrides-result-cs.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
