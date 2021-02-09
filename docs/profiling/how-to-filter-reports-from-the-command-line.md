---
title: 從命令列篩選報表 | Microsoft Docs
description: 使用 VSPerfReport.exe 將報告限制在特定時間週期，或選取的進程和執行緒。 本文列出選項和描述。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dda6b89dcdfacc286417924c666b3ebd805f1cc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897718"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>如何：從命令列篩選報表
使用 **VSPerfReport** 命令的選項，即可將報表篩選到分析資料檔案的特定時間區段，或將資料限制到一或多個處理序或執行緒。 如需此命令的詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。

|選項。|描述|
|-------------|-----------------|
|**StartTime:**[*Value*]|只顯示值 (以毫秒為單位) 之後所收集的資料。|
|**EndTime:**[*Value*]|只顯示值 (以毫秒為單位) 之前所收集的資料。|
|**FilterFile:** `VSPFFile`|指定從 [Visual Studio 效能報告] 視窗所產生之篩選器檔案的位置。|
|**MsFilter:**[*StartTime,Duration*]|只顯示從 `StartTime` 直到 `Duration` 長度(以毫秒為單位) 的資料。|
|**Process:**[*Pid*]|只顯示來自所指定處理序的資料。|
|**Thread:**[*ThreadID*]|只顯示來自所指定執行緒的資料。|
|**Thread:**[*ThreadID,ProcessID*]|只顯示來自與指定處理序建立關聯之指定執行緒的資料。|
