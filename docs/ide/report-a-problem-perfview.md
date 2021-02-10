---
title: 利用 PerfView 收集 ETL 追蹤
ms.date: 09/27/2019
ms.topic: how-to
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 6f0696a24f04d2cba52994c86a3475f56d3e7947
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970708"
---
# <a name="collect-an-etl-trace-with-perfview"></a>利用 PerfView 收集 ETL 追蹤

PerfView 是建立 ETL (事件追蹤記錄檔) 檔案的工具，它是以適合為某些 Visual Studio 問題進行疑難排解的 [Windows 事件追蹤](/windows/desktop/ETW/event-tracing-portal) 為基礎。 當您回報問題時，產品小組偶爾會要求您執行 PerfView 來收集其他資訊。

## <a name="install-perfview"></a>安裝 PerfView

從 [GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md)下載 PerfView。

## <a name="run-perfview"></a>執行 PerfView

1. 在 Windows 檔案總管中以滑鼠右鍵按一下 **PerfView.exe**，然後以系統管理員身分選擇 [以系統管理員身分執行]
1. 在 [收集] 功能表中，選擇 [收集]
1. 勾選 [Zip]、[合併] 和 [ThreadTime]。
1. 將 **循環 MB** 提高到 1000。
1. 如果想要收集多次，請變更 **目前的目錄**，將 ETL 追蹤儲存至指定的資料夾和資料檔案。
1. 若要開始記錄資料，請選擇 [開始收集] 按鈕。
1. 若要停止記錄資料，請選擇 [停止收集] 按鈕。 PrefView.etl.zip 檔案會儲存在指定的目錄。

PerfView 只會儲存適合其緩衝區的最新資料。 因此，請在 Visual Studio 開始凍結或變慢後，嘗試停止收集。 遇到問題後請勿收集超過 30 秒。

如需詳細資訊，請觀看 [Channel9 的 PerfView 教學課程影片](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command)。
