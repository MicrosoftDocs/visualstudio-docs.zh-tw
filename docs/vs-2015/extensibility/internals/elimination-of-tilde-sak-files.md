---
title: 排除 ~ SAK 檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 751acf4e5f56b7b477f05ab71571e0becd566649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838849"
---
# <a name="elimination-of-sak-files"></a>消除 ~SAK 檔案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在原始檔控制外掛程式 API 1.2 中，~ SAK 檔案已取代為功能旗標和新函式，這些函式會偵測原始檔控制外掛程式是否支援 MSSCCPRJ.SCC 檔和共用簽出。  
  
## <a name="sak-files"></a>~ SAK 檔案  
 Visual Studio .NET 2003 建立了首碼為 ~ SAK 的暫存檔案。 這些檔案是用來判斷原始檔控制外掛程式是否支援：  
  
- MSSCCPRJ.SCC。SCC 檔。  
  
- 多 (共用) 簽出。  
  
  如果外掛程式支援原始檔控制外掛程式 API 1.2 中提供的 advanced 函式，IDE 可以使用新功能、旗標和函式來偵測這些功能，而不需建立暫存檔案，如下節所述。  
  
## <a name="new-capability-flags"></a>新功能旗標  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>新函式  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 如果原始檔控制外掛程式支援多個 (共用) 簽出，則會宣告 `SCC_CAP_MULTICHECKOUT` 功能並執行函式 `SccIsMultiCheckOutEnabled` 。 每當任何原始檔控制的專案上發生簽出作業時，就會呼叫此函式。  
  
 如果原始檔控制外掛程式支援建立和使用 MSSCCPRJ.SCC。接著，它會宣告 `SCC_CAP_SCCFILE` 功能並執行 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)。 這個函式會使用檔案清單來呼叫。 函數會傳回 `TRUE/FALSE` 每個檔案，以指出 Visual Studio 是否應使用 mssccprj.scc。它的 SCC 檔。 如果原始檔控制外掛程式選擇不支援這些新功能和函式，則可以使用下列登錄機碼來停用這些檔案的建立：  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateTemporaryFilesInSourceControl" = dword：00000001  
  
> [!NOTE]
> 如果此登錄機碼設定為 dword：00000000，則相當於機碼不存在，而且 Visual Studio 仍會嘗試建立暫存檔案。 但是，如果登錄機碼設定為 dword：00000001，Visual Studio 不會嘗試建立暫存檔案。 相反地，它會假設原始檔控制外掛程式不支援 MSSCCPRJ.SCC。SCC 檔案，且不支援共用簽出。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 1.2 版的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
