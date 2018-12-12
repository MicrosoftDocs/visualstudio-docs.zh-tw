---
title: CreateExpInstance 公用程式 |Microsoft Docs
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
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73a6761e844cee41c1a6f0df79f0d6529f4a8215
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768252"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance 公用程式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用 CreateExpInstance 公用程式建立時，重設，或刪除 Visual Studio 的實驗執行個體。 您可以使用實驗性執行個體，偵錯及測試 Visual Studio 擴充功能，而不需要變更基礎的產品。  
  
## <a name="syntax"></a>語法  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>參數  
 / 建立  
 建立實驗執行個體。  
  
 / 重設  
 刪除實驗的執行個體，並接著會建立一個新。  
  
 /Clean  
 刪除實驗性執行個體。  
  
 / VSInstance  
 包含要複製基底的 Visual Studio 執行個體的目錄名稱。  
  
 / RootSuffix  
 要附加至實驗執行個體目錄的名稱尾碼。  
  
## <a name="remarks"></a>備註  
 當您使用 Visual Studio 擴充功能上時，您可以按 f5 鍵開啟預設的實驗執行個體，然後安裝目前的擴充功能。 如果實驗執行個體功能，Visual Studio 會建立一個具有預設設定。  
  
 實驗執行個體的預設位置取決於 Visual Studio 版本號碼。 例如，Visual Studio 2015 中，位置是 %localappdata%\Microsoft\VisualStudio\14.0Exp\ 目錄位置中的所有檔案會都視為該執行個體的一部分。 除非目錄名稱會變成預設位置，任何其他的實驗性執行個體不會載入 Visual studio。  
  
 在開啟的實驗執行個體時，visual Studio 不會存取系統登錄。 這不同於舊版的 Visual Studio 中，使用的登錄區的實驗性版本。  
  
 CreateExpInstance 公用程式會取代，VsRegEx 公用程式。  
  
 下列範例會重設 Visual Studio 的預設實驗性執行個體。  
  
 **CreateExpInstance.exe /Reset /VSInstance = 14.0 /RootSuffix Exp 的 =**  
  
## <a name="see-also"></a>另請參閱  
 [發行產品](../../misc/releasing-a-visual-studio-integration-product.md)

