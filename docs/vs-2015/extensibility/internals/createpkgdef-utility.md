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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838799"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef 公用程式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

取得 Visual Studio 擴充功能的 .dll 檔作為參數，並建立與 .dll 伴隨的 .pkgdef 檔案。 .Pkgdef 檔案包含在安裝擴充功能時，將寫入系統登錄的所有資訊。  
  
> [!NOTE]
> Visual Studio SDK 中包含的大部分專案範本會在組建程式中自動建立 .pkgdef 檔案。 本檔適用于想要手動建立套件，或轉換現有套件以使用 .pkgdef 部署的使用者。  
  
## <a name="syntax"></a>語法  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>引數  
 /out =`FileName`  
 必要。 將 .pkgdef 輸出檔的名稱設定為 `FileName` 。  
  
 /codebase  
 選擇性。 強制註冊程式碼基底公用程式。  
  
 /assembly  
 強制註冊元件公用程式。  
  
 `AssemblyPath`  
 您要從中產生 .pkgdef 之 .dll 檔案的路徑。  
  
## <a name="remarks"></a>備註  
 使用 .pkgdef 檔案進行擴充部署，會取代舊版 Visual Studio 的登錄需求。  
  
 .Pkgdef 檔案必須安裝在下列其中一個位置：%localappdata%\Microsoft\Visual Studio\14.0\Extensions\ 或%vsinstalldir%\Common7\IDE\Extensions \\ 。 如果安裝資料夾是%localappdata%\Microsoft\Visual Studio\14.0\Extensions，將會 \\ Visual Studio 識別延伸模組，但預設會停用。 使用者可以使用 **擴充功能和更新**來啟用擴充功能。 如果安裝資料夾是%vsinstalldir%\Common7\IDE\Extensions \\ ，則預設會啟用擴充功能。  
  
> [!NOTE]
> [ **擴充功能和更新** ] 工具無法用來存取擴充功能，除非它安裝為 VSIX 封裝的一部分。  
  
## <a name="see-also"></a>另請參閱  
 [CreateExpInstance 公用程式](../../extensibility/internals/createexpinstance-utility.md)
