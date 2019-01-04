---
title: CreatePkgDef 公用程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5c18e77405cd4e48c89d3b481937c7d837488cd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910931"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef 公用程式
採用 Visual Studio 延伸模組做為參數的.dll 檔案，並建立 *.pkgdef*伴隨著檔案 *.dll*檔案。 *.Pkgdef*檔案包含會否則寫入系統登錄時已安裝的延伸模組的所有資訊。  
  
> [!NOTE]
>  建立專案範本會自動包含在 Visual Studio SDK 中的大部分 *.pkgdef*檔案做為建置程序的一部分。 本文件適用於想要以手動的方式，建立封裝，或轉換現有的封裝，若要使用的任何人 *.pkgdef*部署。  
  
## <a name="syntax"></a>語法  
  
```  
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>  
```  
  
## <a name="arguments"></a>引數  
 **/ 出 =&lt;檔名&gt;**  
 必要項。 設定的名稱 *.pkgdef*輸出檔&lt;FileName&gt;。  
  
 **/codebase**  
 選擇性。 強制執行 active directory 註冊**程式碼基底**公用程式。  
  
 **/assembly**  
 強制執行 active directory 註冊**組件**公用程式。  
  
 **&lt;AssemblyPath&gt;**  
 路徑 *.dll*要產生的檔案 *.pkgdef*。  
  
## <a name="remarks"></a>備註  
 使用擴充功能部署 *.pkgdef*檔案會取代舊版的 Visual Studio 的登錄需求。  
  
 *.Pkgdef*檔案必須安裝在下列位置其中之一： 

- *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\* 
 
- *%vsinstalldir%\Common7\IDE\Extensions\\*
    
  如果安裝資料夾 *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*，擴充 Visual Studio 中，將會辨識，但預設會停用。 使用者可以藉由啟用延伸模組**擴充功能和更新**。 
   
  如果安裝資料夾 *%vsinstalldir%\Common7\IDE\Extensions\\*，預設會啟用擴充功能。  
  
> [!NOTE]
>  **擴充功能和更新**工具無法用來存取延伸模組，除非它安裝 VSIX 套件的一部分。  
  
## <a name="see-also"></a>另請參閱  
 [CreateExpInstance 公用程式](../../extensibility/internals/createexpinstance-utility.md)