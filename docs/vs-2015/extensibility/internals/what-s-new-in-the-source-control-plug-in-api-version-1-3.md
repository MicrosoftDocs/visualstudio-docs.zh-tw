---
title: 什麼&#39;的新功能的原始檔控制外掛程式 API 版本 1.3 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58756bde7f3eb9fbc0f42bf494d82e8cc508796e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793915"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>什麼&#39;的新功能的原始檔控制外掛程式 API 版本 1.3
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

原始檔控制外掛程式 API 版本 1.3 導入了下列新的函式，以提供更進階的控制項。  
  
## <a name="changes"></a>變更  
 下列函式是原始檔控制外掛程式 API 版本 1.3 的新項目：  
  
|功能|總覽|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|可讓回報的另一項功能位元|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|允許檔案版本控制資料庫中於本機的磁碟上有較新版本的檢查|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|可讓指定的檔案名稱變更 （重新命名、 新增及刪除） 的狀態檢查|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|可讓目錄和檔案的版本控制資料庫中的檢查|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|將指定的檔案清單從版本控制資料庫加入至目前的專案|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|執行無訊息 「 取得 」 所指定的檔案 （沒有使用者介面會顯示）|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|允許存取使用者特定的選項|  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

