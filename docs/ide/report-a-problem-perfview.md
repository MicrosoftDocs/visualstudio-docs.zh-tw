---
title: 收集使用 PerfView 的 ETL 追蹤
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- perfview
- ETL Trace
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 6b1f61888fa642ed544c6da7d1cf77c43b52b2d9
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461545"
---
# <a name="collect-an-etl-trace-with-perfview"></a>利用 PerfView 收集 ETL 追蹤

PerfView 是建立 ETL (事件追蹤記錄檔) 檔案的工具，它是以適合為某些 Visual Studio 問題進行疑難排解的 [Windows 事件追蹤](/windows/desktop/ETW/event-tracing-portal) 為基礎。 當您回報問題時，產品小組偶爾會要求您執行 PerfView 來收集其他資訊。

## <a name="install-perfview"></a>安裝 PerfView

從 [Microsoft 下載中心](http://www.microsoft.com/download/details.aspx?id=28567)下載 PerfView。

## <a name="run-perfview"></a>執行 PerfView

1. 在 Windows 檔案總管中以滑鼠右鍵按一下 **PerfView.exe**，然後以系統管理員身分選擇 [以系統管理員身分執行] 
1. 在 [收集] 功能表中，選擇 [收集] 
1. 勾選 [Zip]  、[合併]  和 [ThreadTime]  。
1. 將**循環 MB** 提高到 1000。
1. 如果想要收集多次，請變更**目前的目錄**，將 ETL 追蹤儲存至指定的資料夾和資料檔案。
1. 若要開始記錄資料，請選擇 [開始收集]  按鈕。
1. 若要停止記錄資料，請選擇 [停止收集]  按鈕。 PrefView.etl.zip 檔案會儲存在指定的目錄。

PerfView 只會儲存適合其緩衝區的最新資料。 因此，請在 Visual Studio 開始凍結或變慢後，嘗試停止收集。 遇到問題後請勿收集超過 30 秒。

如需詳細資訊，請觀看 [Channel9 的 PerfView 教學課程影片](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command)。
