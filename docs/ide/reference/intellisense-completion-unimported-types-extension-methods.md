---
title: IntelliSense 完成 & 擴充方法的類型
description: 如何針對尚未使用指示詞彙入的類型和延伸方法使用 IntelliSense 完成 `using` 。
ms.custom: SEO-VS-2020
ms.date: 07/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3eb912ebb4d8d7d4596a6aae6499ac054d4514ca
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102502"
---
# <a name="intellisense-completion-for-unimported-types-and-extension-methods"></a>未匯入類型和擴充方法的 IntelliSense 完成

此重構適用於：

- C#

- Visual Basic

事項 **：** IntelliSense 會提供未匯入類型和擴充方法的完成。

時機 **：** 您想要使用在您的專案中已經有相依性的類型或擴充方法，但 using 語句尚未新增至您的檔案。

**原因：** 您不需要手動將 using 語句新增至您的檔案。

## <a name="how-to"></a>使用方法

1. 當您開始輸入在專案中具有相依性之類型或擴充方法的名稱時，IntelliSense 會提供建議。 未匯入命名空間中的專案會將其包含的命名空間顯示為尾碼。

   > [!TIP]
   > 您可以視需要顯示/隱藏未匯入命名空間中的專案，使用 [ **展開] 按鈕 (Alt + A)** 出現在完成清單的左下方。 若要變更預設行為，請移至 [ **工具**  >  **選項**  >  **文字編輯器**  >  **c #**  /  **基本**  >  **IntelliSense** ]，並尋找 **未匯入命名空間中的 [顯示專案** ]。

2. 選取並認可未匯入專案。

   Using 語句會自動加入至您的檔案。

   ![針對未匯入的型別完成 IntelliSense](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>另請參閱

- [IntelliSense](../using-intellisense.md)
- [重構](../refactoring-in-visual-studio.md)
