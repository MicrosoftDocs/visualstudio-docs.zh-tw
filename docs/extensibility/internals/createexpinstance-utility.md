---
title: CreateExpInstance 公用程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1a9f73f396fffe93903f4295428a011c5b5e8d4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042539"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance 公用程式
使用**CreateExpInstance**公用程式來建立、 重設，或刪除 Visual Studio 的實驗執行個體。 您可以使用實驗性執行個體，偵錯及測試 Visual Studio 擴充功能，而不需要變更基礎的產品。  
  
## <a name="syntax"></a>語法  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
## <a name="parameters"></a>參數  
 **/ 建立**建立實驗執行個體。  
  
 **/Reset**  
 刪除實驗的執行個體，並接著會建立一個新。  
  
 **/Clean**  
 刪除實驗性執行個體。  
  
 **/VSInstance**  
 包含要複製基底的 Visual Studio 執行個體的目錄名稱。  
  
 **/RootSuffix**  
 要附加至實驗執行個體目錄的名稱尾碼。  
  
## <a name="remarks"></a>備註  
 當您使用 Visual Studio 擴充功能上時，您可以按 f5 鍵開啟預設的實驗執行個體，然後安裝目前的擴充功能。 如果實驗執行個體功能，Visual Studio 會建立一個具有預設設定。  
  
 實驗執行個體的預設位置取決於 Visual Studio 版本號碼。 例如，Visual Studio 2015 中，位置是 *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*。 目錄位置中的所有檔案都視為該執行個體的一部分。 除非目錄名稱會變成預設位置，任何其他的實驗性執行個體不會載入 Visual studio。  
  
 在開啟的實驗執行個體時，visual Studio 不會存取系統登錄。 這不同於舊版的 Visual Studio 中，使用的登錄區的實驗性版本。  
  
 **CreateExpInstance**公用程式來取代**VsRegEx**公用程式。  
  
 下列範例會重設 Visual Studio 的預設實驗性執行個體：  
  
 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage](../../extensibility/internals/vspackages.md)