---
title: CreatePkgDef 公用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 010ee75efd84f016b0eb68fa9f715102026a4678
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441496"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef 公用程式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

採用 Visual Studio 延伸模組做為參數的.dll 檔案，並建立.pkgdef 檔案隨附此.dll 檔。 .Pkgdef 檔案包含會否則寫入系統登錄時已安裝的延伸模組的所有資訊。  
  
> [!NOTE]
> 大多會自動包含在 Visual Studio SDK 中的專案範本會建立.pkgdef 檔案，做為建置程序的一部分。 本文件適用於想要以手動的方式，建立封裝，或轉換現有的封裝，以使用.pkgdef 部署的任何人。  
  
## <a name="syntax"></a>語法  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>引數  
 /out=`FileName`  
 必要項。 設定的.pkgdef 輸出檔名稱`FileName`。  
  
 /codebase  
 選擇性。 強制使用程式碼基底公用程式的註冊。  
  
 /assembly  
 強制使用組件的公用程式的註冊。  
  
 `AssemblyPath`  
 您要從中產生.pkgdef.dll 檔案的路徑。  
  
## <a name="remarks"></a>備註  
 使用.pkgdef 檔案的延伸模組部署會取代舊版的 Visual Studio 的登錄需求。  
  
 .Pkgdef 檔案必須安裝在下列位置： %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ 或 %vsinstalldir%\Common7\IDE\Extensions\\。 如果的安裝資料夾是 %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\，擴充 Visual Studio 中，將會辨識，但預設會停用。 使用者可以藉由啟用延伸模組**擴充功能和更新**。 如果的安裝資料夾是 %vsinstalldir%\Common7\IDE\Extensions\\，預設會啟用擴充功能。  
  
> [!NOTE]
> **擴充功能和更新**工具無法用來存取延伸模組，除非它安裝 VSIX 套件的一部分。  
  
## <a name="see-also"></a>另請參閱  
 [CreateExpInstance 公用程式](../../extensibility/internals/createexpinstance-utility.md)
