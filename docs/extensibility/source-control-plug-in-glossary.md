---
title: 源代碼管理外掛程式詞彙表 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3835561eb63fa2a4a71174732c07ecd73f1df5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699902"
---
# <a name="source-control-plug-in-glossary"></a>原始檔控制外掛程式字彙表
以下有用的術語和定義與原始程式碼管理外掛程式 SDK 文件相關。

## <a name="definitions"></a>定義
 簽入 當使用者對工作複本進行更改時,用戶必須將更改從工作複本發送到中央原始程式碼管理儲存庫。 這將創建可供其他使用者使用的檔的新修訂版。 此過程稱為簽入。

 簽出從儲存庫請求工作副本的行為,通知存儲庫您修改該副本的意圖。 工作副本反映專案簽出時的狀態。

 用戶端 使用原始程式碼控制系統的程式。 對於本文檔,它是可視化工作室 IDE。

 註釋 描述執行原始碼管理操作時使用者可以附加到修訂版更改的消息。

 衝突兩個用戶嘗試簽入對同一檔的同一區域的更改的情況。 通常,必須執行合併。

 目錄 用戶端本地資料夾稱為目錄。 這是用戶實際進行更改的副本。 給定專案可以有許多工作副本;通常每個開發人員都有自己的副本。

 Get get 操作使用戶的工作副本與存儲庫副本一起更新。 與結帳不同,當使用者只需要最新副本但不打算進行任何更改時,將執行 get。

 歷史記錄 它通常是在原始程式碼管理儲存庫中完成的所有簽出、簽入、更新、標記和版本的摘要。

 IDE 通常是指可視化工作室集成開發環境。 但是,它還可以引用其他用戶端環境來識別原始程式碼管理外掛程式 API。

 合併將兩個或多個原始程式碼檔組合以形成包含以前檔的所有功能的新文件的過程。 在兩個或多個開發人員同時處理檔的版本控制中,這個概念至關重要。

 專案 源控制資料夾通常稱為專案。 這與 Visual Studio 中的專案或解決方案沒有任何關係。

 外掛程式 DLL 透過實源碼管理外掛程式 API 提供原始碼管理功能。

 存儲庫源控制系統存儲專案的完整修訂歷史記錄的主副本。 每個專案都有一個存儲庫。

 修訂 檔或檔集的歷史記錄中已提交的更改。 修訂是不斷更改的專案中的一個快照。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
