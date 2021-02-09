---
title: Spy + + 簡介 |Microsoft Docs
description: 瞭解 Spy + + 調試工具。 顯示系統物件關聯性的圖形樹狀結構。 取得選定視窗、執行緒、進程或訊息的屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eefc69d7dbd7d05eaadc3e9fe8976c0ff03c9a30
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910016"
---
# <a name="introducing-spy"></a>Spy++ 簡介
Spy++ 可讓您執行下列工作︰

- 顯示系統物件關聯性的圖形樹狀結構， 其中包括 [處理序](../debugger/processes-view.md)、 [執行緒](../debugger/threads-view.md)和 [視窗](../debugger/windows-view.md)。

- 搜尋指定的 [視窗](../debugger/how-to-search-for-a-window-in-windows-view.md)、 [執行緒](../debugger/how-to-search-for-a-thread-in-threads-view.md)、 [處理序](../debugger/how-to-search-for-a-process-in-processes-view.md)或 [訊息](../debugger/how-to-search-for-a-message-in-messages-view.md)。

- 檢視所選 [視窗](../debugger/how-to-display-window-properties.md)、 [執行緒](../debugger/how-to-display-thread-properties.md)、 [處理序](../debugger/how-to-display-process-properties.md)或 [訊息](../debugger/how-to-display-message-properties.md)的屬性。

- 直接在檢視中選取視窗、執行緒、處理序或訊息。

- 使用 [搜尋工具](../debugger/how-to-use-the-finder-tool.md) ，依滑鼠指標位置來選取視窗。

- 使用複雜的訊息記錄檔選取參數來設定 [message 選項](../debugger/how-to-open-messages-view-from-find-window.md) 。

  Spy++ 提供工具列和超連結，有助您加快作業。 它也提供 [重新整理]  命令來更新使用中的檢視，[視窗搜尋工具]  讓您更輕鬆地監視，而 [字型]  對話方塊，則可自訂檢視視窗。 此外，Spy++ 可讓您儲存和還原使用者偏好設定。

  您可以在各種 Spy++ 視窗中，按一下滑鼠右鍵顯示常用命令的捷徑功能表。 指標位置可決定要顯示哪些命令。 例如，如果您在 [視窗] 檢視的項目上按一下滑鼠右鍵，會顯示選取的視窗，然後按一下捷徑功能表上的 [反白顯示]  ，則選取視窗的框線就會閃爍，以便更輕鬆地找到該視窗。

> [!NOTE]
> 下列兩個其他公用程式跟 Spy++ 相似：PView，會顯示處理序和執行緒的詳細資料；DDESPY.EXE，可讓您監視動態資料交換 (DDE) 訊息。

## <a name="64-bit-operating-systems"></a>64 位元作業系統
 Spy++ 有兩個版本。 第一個版本名為 Spy++ (spyxx.exe)。如果視窗是在 32 位元處理序中執行，就非常適合用這個版本來顯示傳送至視窗的訊息。 例如，Visual Studio 會在 32 位元處理序中執行。 因此，您可以使用 Spy++ 來顯示傳送至方案總管 的訊息。 由於 Visual Studio 中大多陣列建的預設設定是在32位進程中執行，因此第一版的 Spy + + 就是在 Visual Studio 的 [ **工具** ] 功能表上可用的元件（如果 [已安裝必要元件](../debugger/how-to-start-spy-increment.md)的話）。

 第二個版本名為 Spy++ (64 位元) (spyxx_amd64.exe)。如果視窗是在 64 位元處理序中執行，就非常適合用這個版本來顯示傳送至視窗的訊息。 比方說，在 64 位元作業系統中，[記事本] 會在 64 位元處理序中執行。 因此，您可以使用 Spy++ (64 位元) 來顯示傳送至 [記事本] 的訊息。 Spy++ (64 位元) 通常位於

 ..\\*Visual Studio 安裝資料夾*\Common7\Tools\spyxx_amd64.exe。

 您可以直接從命令列執行任一版本的 Spy++。

> [!NOTE]
> 雖然 Spy++ (64 位元) 的檔案名稱包含 "amd"，但它會在任何 x64 Windows 作業系統上執行。

## <a name="see-also"></a>另請參閱
- [如何：啟動 Spy++](../debugger/how-to-start-spy-increment.md)
- [使用 Spy++](../debugger/using-spy-increment.md)
- [Spy++ 檢視](../debugger/spy-increment-views.md)
- [Spy++ 參考](../debugger/spy-increment-reference.md)