---
title: 產生解構函式的快速動作
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a609b16e0d1bc7e30dc26ef047228a6cacdb46b2
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324733"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>在 Visual Studio 中產生解構函式

此程式碼產生適用於：

- C#

**功能：** 可讓您立即針對新解構函式產生方法虛設常式。

**時機：** 您想要正確地自動解構您的類型。

**原因：** 您可以手動鍵入解構函式，但是此功能將使用正確的輸出參數為您產生虛設常式。

## <a name="generate-deconstructor"></a>產生解構函式

1. 宣告新類型，其具有指定的所需 out 參數。 如果找不到與您宣告相符的解構執行個體，此宣告會造成錯誤。

   ![遺失解構函式錯誤](media/deconstruct.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 將游標放在您的宣告中，然後按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 按一下 ![出現於左邊界的螺絲起子](media/screwdriver.png) 圖示，如果文字游標已經在類別中的空白行上，此圖示就會出現在左邊界上。

      ![產生解構函式程式碼修正](media/deconstruct-codefix.png)

3. 選取 [產生方法 'MyInternalClass.Deconstruct'] 來產生解構函式。

   ![產生的解構函式程式碼](media/deconstruct-result.png)


## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
- [.NET 開發人員的秘訣](../../ide/visual-studio-2017-for-dotnet-developers.md)