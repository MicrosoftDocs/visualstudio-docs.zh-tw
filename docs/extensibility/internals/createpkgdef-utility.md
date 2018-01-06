---
title: "CreatePkgDef 公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 47316f6bd47d5d528dc6e36dfe3a4bcb67e00909
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createpkgdef-utility"></a>CreatePkgDef 公用程式
採用.dll 檔案，以做為參數的 Visual Studio 擴充功能，並建立.dll 伴隨著.pkgdef 檔。 .Pkgdef 檔包含會否則被寫入系統登錄時安裝擴充功能的所有資訊。  
  
> [!NOTE]
>  大部分的自動包含在 Visual Studio SDK 中的專案範本建立.pkgdef 檔做為建置流程的一部分。 這份文件適用於想要以手動方式建立封裝，或轉換使用.pkgdef 部署的現有封裝的人員。  
  
## <a name="syntax"></a>語法  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>引數  
 /out =`FileName`  
 必要。 設定.pkgdef 輸出檔名稱`FileName`。  
  
 /codebase  
 選擇性。 強制使用程式碼基底公用程式的註冊。  
  
 /assembly 選項  
 強制使用組件公用程式的註冊。  
  
 `AssemblyPath`  
 您要產生.pkgdef.dll 檔案的路徑。  
  
## <a name="remarks"></a>備註  
 藉由使用.pkgdef 檔案的延伸模組部署會取代舊版的 Visual Studio 的登錄需求。  
  
 .Pkgdef 檔必須安裝在下列位置之一： %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ 或 %vsinstalldir%\Common7\IDE\Extensions\\。 如果的安裝資料夾是 %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\，擴充功能將無法辨識的 Visual Studio 中，但預設會停用。 使用者可以啟用延伸模組使用**擴充功能和更新**。 如果的安裝資料夾是 %vsinstalldir%\Common7\IDE\Extensions\\，預設會啟用擴充功能。  
  
> [!NOTE]
>  **擴充功能和更新**工具無法用來存取擴充功能，除非它會安裝為 VSIX 套件的一部分。  
  
## <a name="see-also"></a>請參閱  
 [CreateExpInstance 公用程式](../../extensibility/internals/createexpinstance-utility.md)