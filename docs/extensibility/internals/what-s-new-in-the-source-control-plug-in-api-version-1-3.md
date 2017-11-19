---
title: "什麼 &#39;的新原始檔控制外掛程式 API 版本 1.3 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd0c23258034fb99f5e2e4e0c86ca9e61c3d68ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>什麼 &#39; s 原始檔控制外掛程式 API 版本 1.3 的新功能
原始檔控制外掛程式 API 1.3 版導入了下列新的函式，以提供更進階的控制項。  
  
## <a name="changes"></a>變更  
 下列函數是原始檔控制外掛程式 api 1.3 版新功能：  
  
|函式|概觀|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|允許的額外功能來報告的位元|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|允許檢查比本機磁碟上的版本控制資料庫中有較新版本的檔案|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|允許指定的檔案名稱變更 （重新命名、 新增項目和刪除） 的狀態檢查|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|允許的目錄和檔案在版本控制資料庫中的檢查|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|將指定的檔案清單從版本控制資料庫加入至目前的專案|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|執行無訊息 「 取得 」 所指定的檔案 （沒有使用者介面顯示）|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|可讓您存取使用者特定的選項|  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)