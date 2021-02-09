---
title: 產生解構函式的快速動作
description: 瞭解如何使用 [快速動作與重構] 功能表立即產生新解構函式的方法 stub。
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a4c243ab46858a4c8eb944d485900718b685bf5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897967"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>在 Visual Studio 中產生解構函式

此程式碼產生適用於：

- C#

事項 **：** 讓您立即產生新解構函式的方法 stub。

時機 **：** 您想要自動正確地解構您的類型。

**原因：** 您可以手動輸入解構函式，但這項功能會使用正確的輸出參數為您產生存根。

## <a name="generate-a-deconstructor"></a>產生解構函式

1. 宣告新類型，其具有指定的所需 out 參數。 如果找不到與您宣告相符的解構執行個體，此宣告會造成錯誤。

   ![遺失解構函式錯誤](media/deconstruct.png)

2. 採取下列其中一個步驟：

   - **鍵盤**
      - 將游標放在您的宣告中，然後選取 Ctrl+. 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
      - :::image type="icon" source="media/screwdriver.png":::如果文字游標已經在類別中的空白行上，請選取出現在左邊界中的圖示。

      ![產生解構函式程式碼修正](media/deconstruct-codefix.png)

3. 選取 [產生方法 'MyInternalClass.Deconstruct'] 來產生解構函式。

   ![產生的解構函式程式碼](media/deconstruct-result.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
- [.NET 開發人員的秘訣](../csharp-developer-productivity.md)