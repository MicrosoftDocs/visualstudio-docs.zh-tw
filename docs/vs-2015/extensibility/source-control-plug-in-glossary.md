---
title: 原始檔控制外掛程式詞彙 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160597"
---
# <a name="source-control-plug-in-glossary"></a>原始檔控制外掛程式字彙表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

下列有用的詞彙和定義適用于原始檔控制外掛程式 SDK 檔。  
  
## <a name="definitions"></a>定義  
 簽入  
 當使用者對工作複本進行變更時，使用者必須將工作複本的變更傳送到中央原始檔控制儲存機制。 這會建立可供其他使用者使用的新檔案修訂。 此程式稱為「簽入」。  
  
 簽出  
 從存放庫要求工作複本的動作，會通知您意圖的存放庫加以修改。 工作複本會反映出專案在簽出時的狀態。  
  
 用戶端  
 使用原始程式碼控制系統的程式。 基於本檔的目的，這是 Visual Studio IDE。  
  
 註解  
 描述當執行原始檔控制作業時，使用者可以附加至修訂的變更的訊息。  
  
 衝突  
 當兩位使用者嘗試將變更簽入相同檔案的相同區域時，就會發生這種情況。 一般而言，必須執行合併。  
  
 目錄  
 用戶端本機資料夾稱為目錄。 這是使用者實際進行變更的複本。 指定專案可以有許多工作複本;一般來說，每位開發人員都有自己的複本。  
  
 Get  
 取得作業可將使用者的工作複本與存放庫複本保持在最新狀態。 和簽出不同的是，當使用者只需要最新的複本，但打算進行變更時，就會執行 get。  
  
 記錄  
 它通常是在原始檔控制存放庫中完成的所有簽出、簽入、更新、標記和發行的摘要。  
  
 IDE  
 通常是指 Visual Studio 整合式開發環境。 不過，它也可以參考其他辨識原始檔控制外掛程式 API 的用戶端環境。  
  
 合併  
 合併兩個或多個原始程式碼檔案以形成新檔案的程式，其中包含先前檔案的所有功能。 這個概念在版本控制中很重要，因為這兩個或多個開發人員同時處理檔案。  
  
 Project  
 原始檔控制資料夾通常稱為「專案」（project）。 這與 Visual Studio 中的專案或方案沒有任何關聯性。  
  
 外掛程式  
 藉由執行原始檔控制外掛程式 API，提供原始檔控制功能的 DLL。  
  
 Repository  
 原始檔控制系統儲存專案完整修訂歷程記錄的主要複本。 每個專案都只有一個存放庫。  
  
 修訂版  
 檔案或檔案集的歷程記錄中已認可的變更。 修訂是持續變更專案中的一個快照集。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
