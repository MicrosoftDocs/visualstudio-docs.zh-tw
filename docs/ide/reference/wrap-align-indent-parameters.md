---
title: 使參數換行、縮排及對齊
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9c17d5c9d6874c836954941e1fccd8ce9d9f2e3a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149259"
---
# <a name="wrap-indent-and-align-parameters"></a>使參數換行、縮排及對齊

此重構適用於：

- C#

- Visual Basic

**功能：** 使參數換行、縮排及對齊。

**時機：** 您有具多個參數的方法宣告或呼叫。

**原因：** 當一長串參數依照使用者想要的方式換行或縮排後，閱讀起來會更加輕鬆。

## <a name="how-to"></a>操作說明

1. 將游標放在參數清單中。
2. 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。

   ![使參數換行、縮排及對齊](media/wrap-parameters.png)

3. 按 **Enter** 鍵接受重構。

   ![已套用使參數換行、縮排及對齊](media/wrap-parameters-completed.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
