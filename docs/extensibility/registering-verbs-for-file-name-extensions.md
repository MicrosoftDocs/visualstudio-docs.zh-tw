---
title: "註冊副檔名的指令動詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f430486c613e6281404110d4441d2a3d2100534
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="registering-verbs-for-file-name-extensions"></a>註冊副檔名的指令動詞
與應用程式的檔案名稱副檔名關聯通常會有發生於使用者按兩下檔案時的慣用的動作。 這建議動作連結至一個動詞命令，例如開啟時，都會對應至動作。  
  
 您可以註冊使用位於的殼層金鑰在 HKEY_CLASSES_ROOT 是擴充功能的程式設計識別項 (ProgID) 相關聯的動詞命令\\*progid*\shell。 如需詳細資訊，請參閱[檔案類型](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx)。  
  
## <a name="registering-standard-verbs"></a>註冊標準動詞命令  
 作業系統辨識出下列的標準動詞命令：  
  
-   開啟  
  
-   Edit  
  
-   播放  
  
-   的  
  
-   預覽  
  
 可能的話，註冊一個標準動詞。 最常見的方式是開啟的動詞命令。 如果沒有開啟檔案並編輯檔案清楚的差異，請使用編輯動詞命令。 例如，開啟.htm 檔案會顯示它在瀏覽器，而編輯.htm 檔案啟動 HTML 編輯器。 標準指令動詞會當地語系化的作業系統地區設定。  
  
> [!NOTE]
>  註冊標準動詞命令時, 未設定開啟索引鍵的預設值。 預設值包含在功能表上的顯示字串。 作業系統會提供這個標準指令動詞的字串。  
  
 專案檔應該要啟動的新執行個體註冊[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]當使用者在開啟檔案。 下列範例說明標準動詞註冊[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]專案。  
  
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
  
 若要開啟現有的執行個體中的檔案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，註冊 DDEEXEC 索引鍵。 下列範例說明標準動詞註冊[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].cs 檔案中。  
  
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
  
## <a name="setting-the-default-verb"></a>設定預設的動詞命令  
 預設動作是使用者按兩下 Windows 檔案總管 中的檔案時所執行的動作。 預設的動詞命令為動詞命令指定的預設值為 HKEY_CLASSES_ROOT\\*progid*\Shell 索引鍵。 如果未不指定任何值，這個預設動作是 HKEY_CLASSES_ROOT 中指定的第一個指令動詞\\*progid*\Shell 索引鍵清單。  
  
> [!NOTE]
>  如果您想要變更預設的並存部署中的延伸模組的動詞命令，請考慮對安裝與移除的影響。 在安裝期間會覆寫原始的預設值。  
  
## <a name="see-also"></a>另請參閱  
 [管理並存的檔案關聯](../extensibility/managing-side-by-side-file-associations.md)