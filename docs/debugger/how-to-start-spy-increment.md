---
title: 如何-啟動 Spy + + |Microsoft Docs
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b659350adc39fd1088964976b8bcdef629bad44b
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349000"
---
# <a name="how-to-start-spy"></a>如何：啟動 Spy++

您可以從 Visual Studio 或在命令提示字元中啟動 Spy + +。

 當您啟動 Spy + + 時，如果顯示訊息要求變更電腦的許可權，請選取 **[是]**。

> [!NOTE]
> 您只能執行一個 Spy + + 的實例。 如果您嘗試啟動第二個實例，它只會導致目前正在執行的實例取得焦點。

## <a name="prerequisites"></a>必要條件

Spy + + 需要下列元件。 您可以選取 [**個別元件**] 索引標籤，然後選取下列元件，從 [Visual Studio 安裝程式中選取這些元件。

* 在 [偵錯工具和測試] 底下，選取 **[c + + 分析工具]**
* 在 [開發活動] 底下，選取 [ **c + + 核心功能**]

如果您進行了任何變更，請依照提示來安裝這些元件。

## <a name="start-spy-from-visual-studio"></a>從 Visual Studio 啟動 Spy + +

在 [**工具**] 功能表上，選取 [ **Spy + +**]。

因為 Spy + + 會獨立執行，所以在您啟動它之後，您就可以關閉 Visual Studio。

> [!NOTE]
> 當您使用 Spy + + 記錄訊息時，可能會導致作業系統的執行速度變慢。

## <a name="start-spy-at-a-command-prompt"></a>在命令提示字元中啟動 Spy + +

1. 在 [命令提示字元] 視窗中，將目錄變更為包含 spyxx.exe 的資料夾。 一般而言，此資料夾的路徑為.。 \\*Visual Studio 安裝資料夾*\Common7\Tools \\ 。

2. 輸入**spyxx.exe**。

## <a name="see-also"></a>另請參閱
- [使用 Spy++](../debugger/using-spy-increment.md)
- [Spy++ 檢視](../debugger/spy-increment-views.md)
- [Spy++ 參考](../debugger/spy-increment-reference.md)
