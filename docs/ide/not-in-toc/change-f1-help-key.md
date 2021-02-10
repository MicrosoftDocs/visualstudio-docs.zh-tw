---
title: 變更 F1 說明鍵
description: 說明如何重新對應或移除 F1 鍵對應
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
robots: noindex,nofollow
manager: jmartens
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 30073b31fb98f604313c8de5d45687f3f768a374
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961686"
---
# <a name="change-the-f1-help-key-in-visual-studio"></a>變更 Visual Studio 中的 F1 說明鍵

如果您想要將 F1 鍵用於與 F1 說明服務不同的函式，或您只想要使用 F1 停用說明，則可以移除或修改按鍵對應。

> [!IMPORTANT]
> 如果您想要停用 F1 說明，因為效能問題，建議您暫時修改按鍵對應，以便在 Visual Studio 的更新中測試 F1 說明服務的改進。 在大部分的情況下，F1 是從程式碼編輯器開啟語言關鍵字和 Api 參考頁面的簡單方法，或是開啟與 IDE 中的 windows 或 UI 元素相關聯的說明頁面。 如果您停用它，就會將它停用於 Visual Studio 內的所有用途。

**若要停用 F1 說明：**

1. 在 Visual Studio 中，選取 [**工具**  >  **選項**]，然後選取 [**環境**] 下的 [**鍵盤**]。

1. 在 [ **顯示包含** 文字方塊的命令] 方塊中，輸入 **Help. f1** 以篩選命令的視圖。

   ![停用 F1 說明](../not-in-toc/media/disable-f1-help-key.png)

1. 選取 [ **移除** ] 以移除金鑰組應。

1. 選取 [ **按快速鍵** ] 文字方塊。

1. 在您的鍵盤上，按下 F1 說明的新按鍵或按鍵組合（例如 **Alt + F1**），選取 [ **指派**]，然後選取 **[確定]**。

如需設定鍵盤快速鍵的詳細資訊，請參閱 [識別及自訂鍵盤快速鍵](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。
