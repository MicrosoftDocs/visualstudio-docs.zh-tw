---
title: "消除 ~ SAK 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e487acefcb06c4fa0cd2070bfcf20bd065d500ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="elimination-of-sak-files"></a>消除 ~ SAK 檔案
在原始檔控制外掛程式 API 1.2 ~ SAK 檔案已由功能旗標和偵測原始檔控制外掛程式支援 MSSCCPRJ 檔案，並在共用簽出的新函式取代。  
  
## <a name="sak-files"></a>~ SAK 檔案  
 Visual Studio.NET 2003 中建立暫存檔案前面加上 ~ SAK。 這些檔案可用來判斷是否要支援原始檔控制外掛程式：  
  
-   MSSCCPRJ。SCC 檔案。  
  
-   多個 （共用） 的簽出。  
  
 外掛程式的支援提供的進階函式在原始檔控制外掛程式 API 1.2，IDE 可以偵測到這些功能，而不需要建立透過使用新功能、 旗標和函式，在下列各節詳細的暫存檔案。  
  
## <a name="new-capability-flags"></a>新的功能旗標  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>新的函式  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 如果原始檔控制外掛程式支援多重 （共用） 的簽出，則它會宣告`SCC_CAP_MULTICHECKOUT`功能，而且會實作`SccIsMultiCheckOutEnabled`函式。 在任何原始檔控制專案的簽出作業發生時，會呼叫此函數。  
  
 如果原始檔控制外掛程式支援建立和使用 MSSCCPRJ。SCC 檔案，則它會宣告`SCC_CAP_SCCFILE`功能，而且會實作[SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)。 呼叫此函式的檔案清單。 此函數會傳回`TRUE/FALSE`每個檔案，表示 Visual Studio 是否應該使用 MSSCCPRJ。它的 SCC 檔案。 如果原始檔控制外掛程式選擇不支援這些新功能和函數，它可以使用下列登錄機碼以停用這些檔案的建立：  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]「 DoNotCreateTemporaryFilesInSourceControl"= dword: 00000001  
  
> [!NOTE]
>  如果這個登錄機碼設定為 dword: 00000000，它相當於索引鍵不存在，要與 Visual Studio 仍會嘗試建立暫存檔案。 不過，如果登錄機碼設為 dword: 00000001，Visual Studio 不會嘗試建立暫存檔案。 而是它會假設原始檔控制外掛程式不支援 MSSCCPRJ。SCC 檔案並不支援共用簽出。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)