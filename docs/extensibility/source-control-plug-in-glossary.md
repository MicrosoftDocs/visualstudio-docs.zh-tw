---
title: "原始檔控制外掛程式詞彙 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc45c47f47fe18bc857715acc3948561f06e718c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-in-glossary"></a>原始檔控制外掛程式詞彙
下列很有幫助的詞彙和定義適用於原始檔控制外掛程式 SDK 文件。  
  
## <a name="definitions"></a>定義  
 簽入  
 當使用者變更工作複本時，使用者必須將變更傳送到中央的原始檔控制儲存機制的工作副本。 這會建立新的修訂，可供其他使用者的檔案。 此程序稱為 「 簽入 」。  
  
 簽出  
 要求從儲存機制，通知您試圖修改它的儲存機制的工作複本的動作。 工作複本會反映集會簽出專案的狀態。  
  
 用戶端  
 使用原始程式碼控制系統的程式。 這份文件，它是 Visual Studio IDE。  
  
 註解  
 描述變更原始檔控制作業執行時，使用者可以連接的修訂版本的訊息。  
  
 衝突  
 當兩個使用者嘗試變更簽入至相同的區域相同檔案的狀況。 一般而言，您必須執行合併。  
  
 Directory  
 用戶端的本機資料夾稱為目錄。 這是在其中使用者實際進行變更的複本。 可以有許多工作複本的指定的專案。通常每位開發人員都有自己的複本。  
  
 取得  
 「 取得 」 作業會使使用者的工作複本最新狀態以儲存機制的複本。 不像簽出，使用者只需要最新的複本，但對於要不進行任何變更時，會執行 get。  
  
 歷程  
 它通常是所有簽出、 簽入、 更新、 標記和版本在原始檔控制儲存機制中完成的摘要。  
  
 IDE  
 通常是指在 Visual Studio 整合式開發環境。 不過，它也無法參考到其他辨識原始檔控制外掛程式 API 的用戶端環境。  
  
 合併  
 程序期間的兩個或多個來源的程式碼檔案結合以形成新的檔案，其中包含舊檔案的所有功能。 這個概念非常重要版本控制中，兩個或多個開發人員在檔案上同時處理。  
  
 專案  
 原始檔控制資料夾通常稱為專案。 這在 Visual Studio 中沒有任何關聯性與專案或方案。  
  
 外掛程式  
 藉由實作原始檔控制外掛程式 API 提供原始檔控制功能的 DLL。  
  
 儲存機制  
 在原始檔控制系統的主要複本會儲存在專案的完整修訂歷程記錄。 每個專案都有一個儲存機制。  
  
 修訂  
 檔案歷程記錄或一組檔案中的認可的變更。 修訂是其中一個快照集的不斷變更的專案。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)