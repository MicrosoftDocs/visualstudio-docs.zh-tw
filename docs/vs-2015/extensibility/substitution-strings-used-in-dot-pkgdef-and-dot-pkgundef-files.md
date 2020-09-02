---
title: 中使用的替代字串。.Pkgdef 和。.Pkgundef Files |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47434d9d1dfcedeeaea330b1d65645d7a632c6e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160544"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>在 .Pkgdef 和 .Pkgundef 檔案中使用的替代字串
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用下面所列的替代字串，在您為 Visual Studio 獨立模式 shell 應用程式定義的. .pkgdef 和. .pkgundef 檔案中使用。  
  
## <a name="substitution-strings"></a>替代字串  
  
|String|描述|  
|------------|-----------------|  
|$=*RegistryEntry*$|*RegistryEntry*專案的值。 如果登錄專案字串以反斜線 () ，則會使用登錄子機碼的 \\ 預設值。 例如，替代字串 $ = HKEY_CURRENT_USER \Environment\TEMP $ 會展開至目前使用者的暫存資料夾。|  
|$AppName $|傳遞給 AppEnv.dll 進入點的應用程式限定名稱。 限定名稱是由應用程式的名稱、底線，以及應用程式自動化物件 (CLSID) 所組成，也會記錄為 .pkgdef 檔案中 ThisVersionDTECLSID 設定的值。|  
|$AppDataLocalFolder|此應用程式的% LOCALAPPDATA% 下的子資料夾。|  
|$BaseInstallDir $|安裝 Visual Studio 之位置的完整路徑。|  
|$CommonFiles $|% CommonProgramFiles% 環境變數的值。|  
|$MyDocuments $|目前使用者之我的檔資料夾的完整路徑。|  
|$PackageFolder $|目錄的完整路徑，其中包含應用程式的封裝元件檔。|  
|$ProgramFiles $|% ProgramFiles% 環境變數的值。|  
|$RootFolder $|應用程式根目錄的完整路徑。|  
|$RootKey $|應用程式的根登錄機碼。 根據預設，根目錄位於 HKEY_CURRENT_USER \software \\ *公司* \\ *名稱* \\ *VersionNumber* (當應用程式正在執行時，_Config 會附加到這個機碼) 。 它是由 .pkgdef 檔案 *中的 RegistryRoot*值所設定。<br /><br /> $RootKey $ 字串可以用來取得應用程式子機碼底下的登錄值。 例如，字串 "$ = $RootKey $ \AppIcon $" 會在應用程式根目錄子機碼下傳回 AppIcon 專案的值。<br /><br /> 剖析器會依序處理 .pkgdef 檔案，而且只有在先前已定義專案時，才能存取應用程式子機碼下的登錄專案。|  
|$ShellFolder $|安裝 Visual Studio 之位置的完整路徑。|  
|$System $|Windows\system32 資料夾。|  
|$WINDIR $|Windows 資料夾。|  
  
 如果剖析器無法辨識替代字串或無法判斷登錄專案或環境變數的值，則不會在該部分的字串上執行替代。
