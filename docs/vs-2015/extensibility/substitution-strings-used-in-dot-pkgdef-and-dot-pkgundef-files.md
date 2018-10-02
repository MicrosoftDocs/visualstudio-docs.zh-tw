---
title: 中所使用的替代字串。Pkgdef 和。Pkgundef 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24996e4e32ab86af46fce5280947719f906ffc3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498872"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>中所使用的替代字串。Pkgdef 和。Pkgundef 檔案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新版本位於[中使用的替代字串。Pkgdef 和。Pkgundef 檔案](https://docs.microsoft.com/visualstudio/extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files)。  
  
您可以使用替代下列字串在.pkgdef 和.pkgundef 檔案，您可以為您的 Visual Studio 定義獨立 shell 應用程式。  
  
## <a name="substitution-strings"></a>替代字串  
  
|String|描述|  
|------------|-----------------|  
|$=*RegistryEntry*$|值*RegistryEntry*項目。 如果登錄項目字串結尾的反斜線 (\\)，則會使用登錄子機碼的預設值。 例如，替代字串 $= 的 HKEY_CURRENT_USER\Environment\TEMP$ 會展開至目前使用者的暫存資料夾。|  
|$AppName $|傳遞至 AppEnv.dll 進入點的應用程式限定的名稱。 限定的名稱是由應用程式名稱、 底線和應用程式的自動化物件，也會記錄為 ThisVersionDTECLSID 設定專案.pkgdef 檔中的值的類別識別項 (CLSID) 所組成。|  
|$AppDataLocalFolder|此應用程式的 %LOCALAPPDATA%之下的子資料夾。|  
|$BaseInstallDir $|Visual Studio 安裝的所在位置的完整路徑。|  
|$CommonFiles $|%Commonprogramfiles%環境變數的值。|  
|$MyDocuments $|目前使用者的 [我的文件] 資料夾的完整路徑。|  
|$PackageFolder $|包含應用程式的封裝組件檔案的目錄完整路徑。|  
|$ProgramFiles $|%Programfiles%環境變數的值。|  
|$RootFolder $|應用程式的根目錄完整路徑。|  
|$RootKey $|應用程式的根登錄機碼。 預設的根目錄就是在 HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*VersionNumber* （當應用程式正在執行，_Config 會附加至這個索引鍵。） 它由 RegistryRoot 值中設定*SolutionName*.pkgdef 檔。<br /><br /> $RootKey$ 字串可用來擷取應用程式子機碼下的登錄值。 例如，字串"$= $RootKey$ \AppIcon$"會傳回應用程式根目錄的子機碼下 Assets.xcassets 項目的值。<br /><br /> 剖析器依序處理.pkgdef 檔案，並只有在先前已定義的項目，才能存取應用程式子機碼下的登錄項目|  
|$ShellFolder $|Visual Studio 安裝的所在位置的完整路徑。|  
|$System $|Windows\system32 資料夾中。|  
|$WINDIR $|[Windows] 資料夾中。|  
  
 如果剖析器無法辨識替代字串，或無法判斷登錄項目或環境變數的值，則它不會執行替代字串的一部分。

