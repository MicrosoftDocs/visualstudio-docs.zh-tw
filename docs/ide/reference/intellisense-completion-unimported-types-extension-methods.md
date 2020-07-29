---
title: 未匯入類型和擴充方法的 IntelliSense 完成
description: 如何針對尚未使用指示詞彙入的類型和擴充方法使用 IntelliSense 完成 `using` 。
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
ms.openlocfilehash: d6112bc3894424b9dfd3d060ed390960243b0f98
ms.sourcegitcommit: 4a77403b6bd33c5a6e66a3eefd42c81c39fb67ca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87330982"
---
# <a name="intellisense-completion-for-unimported-types-and-extension-methods"></a>未匯入類型和擴充方法的 IntelliSense 完成

此重構適用於：

- C#

- Visual Basic

**功能：** IntelliSense 會提供未匯入類型和擴充方法的完成。

時機 **：** 您想要使用已經在專案中具有相依性的類型或擴充方法，但是 using 語句尚未新增至您的檔案。 

**原因：** 您不需要手動將 using 語句新增至檔案。

## <a name="how-to"></a>操作方式

1. 當您開始輸入在專案中具有相依性之類型或擴充方法的名稱時，IntelliSense 會提供您建議。 未匯入命名空間中的專案會將其包含的命名空間顯示為尾碼。

   > [!TIP]
   > 您可以使用出現在完成清單左下方的**展開按鈕（Alt + A）** ，視需要顯示/隱藏未匯入命名空間中的專案。 若要變更預設行為，請移至 [**工具**] [選項] [  >  **Options**  >  **文字編輯器**] [  >  **c #**  /  **基本**  >  **IntelliSense** ]，然後尋找 [**從未匯入命名空間顯示專案**

2. 選取並認可未匯入專案。 

   Using 語句會自動新增至您的檔案。

   ![針對未匯入的型別完成 IntelliSense](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>另請參閱

- [IntelliSense](../using-intellisense.md)
- [重構](../refactoring-in-visual-studio.md)
