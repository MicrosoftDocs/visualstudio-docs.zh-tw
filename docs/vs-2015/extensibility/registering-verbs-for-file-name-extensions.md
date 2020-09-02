---
title: 註冊檔案名副檔名的動詞 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dbd97310163a4eb3ae5502c6341dc73322ca653d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685274"
---
# <a name="registering-verbs-for-file-name-extensions"></a>註冊適用於副檔名的動詞命令
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

副檔名與應用程式的關聯通常會有使用者按兩下檔案時所發生的慣用動作。 這個慣用的動作會連結至對應至動作的動詞，例如 open。  
  
 您可以使用位於 HKEY_CLASSES_ROOT ProgID \shell. 的 Shell 機碼，在擴充功能中註冊與程式設計識別碼相關聯的動詞命令 (ProgID) \\ *progid* 如需詳細資訊，請參閱 [檔案類型](https://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx)。  
  
## <a name="registering-standard-verbs"></a>註冊標準動詞  
 作業系統會辨識下列標準動詞：  
  
- 開啟  
  
- 編輯  
  
- 播放  
  
- 列印  
  
- 預覽  
  
  請盡可能註冊標準動詞。 最常見的選擇是開啟的動詞命令。 只有在開啟檔案和編輯檔案之間有明顯的差異時，才使用編輯動詞。 例如，開啟 .htm 檔案時，它會在瀏覽器中顯示，而編輯 .htm 檔則會啟動 HTML 編輯器。 標準動詞會以作業系統地區設定來當地語系化。  
  
> [!NOTE]
> 註冊標準動詞時，請勿設定 Open 鍵的預設值。 預設值包含功能表上的顯示字串。 作業系統會為標準動詞提供這個字串。  
  
 當使用者開啟檔案時，應該註冊專案檔，以啟動的新實例 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 下列範例說明專案的標準動詞註冊 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 。  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 若要在現有的實例中開啟檔案 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，請註冊 DDEEXEC 金鑰。 下列範例說明適用于 .cs 檔案的標準動詞註冊 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 。  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## <a name="setting-the-default-verb"></a>設定預設動詞  
 預設動詞命令是使用者按兩下 Windows 檔案總管中的檔案時，所執行的動作。 預設動詞是指定為 HKEY_CLASSES_ROOT progid \Shell 索引鍵之預設值的動詞 \\ * *。 如果未指定任何值，預設動詞是 HKEY_CLASSES_ROOT \\ *progid*\Shell 索引鍵清單中指定的第一個動詞。  
  
> [!NOTE]
> 如果您打算在並存部署中變更擴充功能的預設動詞，請考慮安裝和移除的影響。 在安裝期間，會覆寫原始預設值。  
  
## <a name="see-also"></a>另請參閱  
 [管理並存的檔案關聯](../extensibility/managing-side-by-side-file-associations.md)
