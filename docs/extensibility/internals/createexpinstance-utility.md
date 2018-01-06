---
title: "CreateExpInstance 公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c1104ebfbd066ad438262fcca0186acfb3854dbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createexpinstance-utility"></a>CreateExpInstance 公用程式
使用 CreateExpInstance 公用程式建立時，重設，或刪除的 Visual Studio 的實驗執行個體。 偵錯及測試 Visual Studio 擴充功能，而不需要變更基礎產品，您可以使用實驗性執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>參數  
 / 建立  
 建立的實驗執行個體。  
  
 / 重設  
 刪除的實驗執行個體，並接著會建立一個新。  
  
 /Clean  
 刪除實驗執行個體。  
  
 /Vsinstance  
 包含要複製基底的 Visual Studio 執行個體的目錄名稱。  
  
 /Rootsuffix  
 要附加至實驗執行個體目錄的名稱尾碼。  
  
## <a name="remarks"></a>備註  
 當您使用 Visual Studio 擴充功能上時，您可以按 f5 鍵開啟預設的實驗執行個體，然後安裝目前的擴充功能。 如果沒有實驗執行個體功能，Visual Studio 會建立一個具有預設設定。  
  
 實驗執行個體的預設位置取決於 Visual Studio 版本號碼。 例如，Visual Studio 2015 中，位置是 %localappdata%\Microsoft\VisualStudio\14.0Exp\ 目錄位置中的所有檔案會都視為該執行個體的一部分。 除非變更預設位置的目錄名稱，否則任何額外的實驗執行個體將不載入由 Visual Studio。  
  
 Visual Studio 開啟實驗執行個體時，不會存取系統登錄。 這不同於舊版的 Visual Studio 中，使用的登錄區的實驗版本。  
  
 CreateExpInstance 公用程式會取代，VsRegEx 公用程式。  
  
 下列範例會重設 Visual Studio 的預設實驗執行個體。  
  
 **CreateExpInstance.exe /Reset /VSInstance = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>請參閱  
 [VSPackage](../../extensibility/internals/vspackages.md)