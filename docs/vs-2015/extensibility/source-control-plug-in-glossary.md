---
title: 原始檔控制外掛程式字彙表 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5120a5c6678cac32ef65e08ef7dc34649364cf9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942185"
---
# <a name="source-control-plug-in-glossary"></a>原始檔控制外掛程式字彙表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

下列實用的詞彙和定義相關的原始檔控制外掛程式 SDK 文件。  
  
## <a name="definitions"></a>定義  
 簽入  
 當使用者變更的工作複本時，使用者必須將變更傳送至中央的原始檔控制儲存機制的工作複本。 這會建立新的修訂其他使用者皆可使用的檔案。 此程序稱為簽入。  
  
 簽出  
 要求的工作複本從儲存機制，通知您試圖修改它的儲存機制的動作。 工作複本會反映集會簽出專案的狀態。  
  
 用戶端  
 使用原始程式碼控制系統的程式。 為了進行本文件中，它是 Visual Studio IDE。  
  
 註解  
 描述使用者可以將附加至修訂原始檔控制作業執行時變更的訊息。  
  
 衝突  
 當兩個使用者嘗試變更簽入至相同的區域相同檔案的情況。 一般而言，您必須執行合併。  
  
 Directory  
 用戶端的本機資料夾稱為 「 目錄 」。 這是在其中的使用者實際上進行變更的複本。 可以有許多的指定的專案; 的工作複本通常每位開發人員都有自己的複本。  
  
 取得  
 「 取得 」 作業會將使用者的工作複本最新的存放庫複本。 不同於簽出，使用者只需要最新的複本，但想要不進行任何變更時，會執行 get。  
  
 歷程  
 它通常是所有簽出、 簽入、 更新、 標籤及進行原始檔控制儲存機制中發行的摘要。  
  
 IDE  
 通常是指在 Visual Studio 整合式開發環境。 不過，它也無法參考其他辨識原始檔控制外掛程式 API 的用戶端環境。  
  
 合併  
 程序期間的兩個或多個來源的程式碼檔案結合以形成新的檔案，其中包含所有的功能，從先前的檔案。 這個概念非常重要版本控制中，兩個或多個開發人員在檔案上同時處理。  
  
 專案  
 原始檔控制資料夾通常稱為專案。 這在 Visual Studio 中沒有任何與專案或方案的關聯性。  
  
 外掛程式  
 藉由實作原始檔控制外掛程式 API 提供原始檔控制功能的 DLL。  
  
 儲存機制  
 原始檔控制系統的其中的主要複本會儲存專案的完整的修訂歷程記錄。 每個專案都只有一個存放庫。  
  
 修訂  
 中的檔案歷程記錄或一組檔案已認可的變更。 修訂是其中一個快照集的持續變更的專案。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
