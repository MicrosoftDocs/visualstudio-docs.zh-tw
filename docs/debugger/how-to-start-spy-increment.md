---
title: 啟動 Spy + + |Microsoft Docs
description: 瞭解如何從 Visual Studio 啟動 Spy + + 工具，或在您想要將方案進行偵測時，于命令提示字元上啟動。
ms.custom: SEO-VS-2020
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0e8b1125534e52c810f97c91bd00ea53dfd3d6de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896623"
---
# <a name="how-to-start-spy"></a>如何：啟動 Spy++

您可以從 Visual Studio 或命令提示字元啟動 Spy + +。

 當您啟動 Spy + + 時，如果顯示訊息以要求對電腦進行變更的許可權，請選取 **[是]**。

> [!NOTE]
> 您只能執行一個 Spy + + 實例。 如果您嘗試啟動第二個實例，它只會讓目前執行中的實例取得焦點。

## <a name="prerequisites"></a>必要條件

Spy + + 需要下列元件。 您可以選取 [ **個別元件** ] 索引標籤，然後選取下列元件，從 Visual Studio 安裝程式選取這些元件。

* 在 [偵錯工具和測試] 底下，選取 **[c + + 分析工具]**
* 在開發活動底下，選取 **c + + 核心功能**

如果您進行了任何變更，請遵循提示來安裝這些元件。

## <a name="start-spy-from-visual-studio"></a>從 Visual Studio 啟動 Spy + +

在 [ **工具** ] 功能表上，選取 [ **Spy + +**]。

因為 Spy + + 獨立執行，所以在您啟動它之後，就可以關閉 Visual Studio。

> [!NOTE]
> 當您使用 Spy + + 記錄訊息時，可能會導致作業系統執行得更慢。

## <a name="start-spy-at-a-command-prompt"></a>在命令提示字元中啟動 Spy + +

1. 在 [命令提示字元] 視窗中，將目錄變更為包含 spyxx.exe 的資料夾。 一般而言，此資料夾的路徑為。 \\*Visual Studio 安裝資料夾*\Common7\Tools \\ 。

2. 輸入 **spyxx.exe**。

## <a name="see-also"></a>另請參閱
- [使用 Spy++](../debugger/using-spy-increment.md)
- [Spy++ 檢視](../debugger/spy-increment-views.md)
- [Spy++ 參考](../debugger/spy-increment-reference.md)
