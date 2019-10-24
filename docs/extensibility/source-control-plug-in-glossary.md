---
title: 原始檔控制外掛程式詞彙 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 672a96c31137a52f3bd4a8c826cef1b19406790b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719578"
---
# <a name="source-control-plug-in-glossary"></a>原始檔控制外掛程式字彙表
下列有用的詞彙和定義適用于原始檔控制外掛程式 SDK 檔。

## <a name="definitions"></a>定義
 簽入當使用者變更工作複本時，使用者必須將工作複本的變更傳送到中央原始檔控制存放庫。 這會建立可供其他使用者使用之檔案的新修訂。 此程式稱為「簽入」。

 簽出從存放庫要求工作複本的動作，通知存放庫您的意圖加以修改。 工作複本會反映專案在簽出時的狀態。

 用戶端：使用原始程式碼控制系統的程式。 基於本檔的目的，這是 Visual Studio 的 IDE。

 批註訊息，描述當執行原始檔控制作業時，使用者可以附加到修訂的變更。

 當兩個使用者嘗試將變更簽入相同檔案的相同區域時，就會發生衝突。 通常，必須執行合併。

 目錄：用戶端本機資料夾稱為目錄。 這是使用者實際進行變更的複本。 指定的專案可以有許多工作複本;一般來說，每位開發人員都有自己的複本。

 取得「取得」作業會使用存放庫複本，將使用者的工作複本帶入最新狀態。 與簽出不同的是，當使用者只需要最新的複本，但打算不進行任何變更時，就會執行 get。

 歷程記錄通常是在原始檔控制存放庫中完成的所有簽出、簽入、更新、標記和發行的摘要。

 IDE 通常是指 Visual Studio 的整合式開發環境。 不過，它也可以參考可辨識原始檔控制外掛程式 API 的其他用戶端環境。

 合併兩個或多個原始程式碼檔案結合的進程，以形成新的檔案，其中包含先前檔案中的所有功能。 這個概念在版本控制中很重要，因為兩個或多個開發人員會同時處理檔案。

 專案：原始檔控制資料夾通常稱為「專案」（project）。 這與 Visual Studio 中的專案或方案沒有任何關聯性。

 外掛程式 DLL，藉由執行原始檔控制外掛程式 API 來提供原始檔控制功能。

 存放庫：原始檔控制系統用來儲存專案完整歷程記錄的主要複本。 每個專案都只有一個存放庫。

 修訂在檔案或一組檔案的歷程記錄中，已認可的變更。 修訂是持續變更專案中的一個快照集。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)