---
title: 產生解構函式的快速動作
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5a3a89d15d05b44575fede98d3043d706b24c1d9
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531890"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>在 Visual Studio 中產生解構函式

此程式碼產生適用於：

- C#

**功能：** 可讓您立即針對新解構函式產生方法虛設常式。

**時機：** 您想要正確地自動解構您的類型。

**原因：** 您可以手動鍵入解構函式，但是此功能會使用正確的輸出參數為您產生虛設常式。

## <a name="generate-a-deconstructor"></a>產生解構函式

1. 宣告新類型，其具有指定的所需 out 參數。 如果找不到與您宣告相符的解構執行個體，此宣告會造成錯誤。

   ![遺失解構函式錯誤](media/deconstruct.png)

2. 採取下列其中一個步驟：

   - **鍵盤**
      - 將游標放在您的宣告中，然後選取 Ctrl+. 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - 選取 ![出現於左邊界的螺絲起子](media/screwdriver.png) 圖示，如果文字游標已經在類別中的空白行上，此圖示就會出現在左邊界上。

      ![產生解構函式程式碼修正](media/deconstruct-codefix.png)

3. 選取 [產生方法 'MyInternalClass.Deconstruct'] 來產生解構函式。

   ![產生的解構函式程式碼](media/deconstruct-result.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
- [.NET 開發人員的秘訣](../csharp-developer-productivity.md)