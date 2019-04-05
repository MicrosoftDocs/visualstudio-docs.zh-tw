---
title: 註冊副檔名的動詞命令 |Microsoft Docs
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
ms.openlocfilehash: ff021643313d267cc92d2f08afa8f41a3ce806b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945551"
---
# <a name="registering-verbs-for-file-name-extensions"></a>註冊適用於副檔名的動詞命令
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

與應用程式的檔案名稱副檔名關聯通常會有偏好的動作，當使用者按兩下檔案時，就會發生。 此建議動作連結到動詞，例如開啟時，對應至動作。  
  
 您可以註冊在 HKEY_CLASSES_ROOT 使用 Shell 機碼位於與擴充功能的程式設計識別項 (ProgID) 相關聯的動詞\\*progid*\shell。 如需詳細資訊，請參閱 <<c0> [ 檔案類型](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx)。  
  
## <a name="registering-standard-verbs"></a>註冊標準動詞命令  
 作業系統可辨識下列的標準動詞命令：  
  
- 開啟  
  
- 編輯  
  
- 播放  
  
- 的  
  
- 預覽  
  
  可能的話，請註冊一個標準動詞。 最常見的方式是開啟的動詞命令。 只有當沒有清楚的差異開啟檔案，並編輯檔案，請使用編輯動詞命令。 例如，開啟的.htm 檔案被它顯示在瀏覽器中，而編輯的.htm 檔案被啟動 HTML 編輯器。 標準動詞命令已當地語系化的作業系統地區設定。  
  
> [!NOTE]
>  註冊時的標準動詞，未設定開啟的索引鍵的預設值。 預設值會包含在功能表上的顯示字串。 作業系統會提供這個標準動詞命令的字串。  
  
 專案檔應該要啟動的新執行個體註冊[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]當使用者在開啟的檔案。 下列範例說明的標準動詞註冊[!INCLUDE[csprcs](../includes/csprcs-md.md)]專案。  
  
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
  
 若要在現有的執行個體中開啟檔案[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，註冊 DDEEXEC 金鑰。 下列範例說明的標準動詞註冊[!INCLUDE[csprcs](../includes/csprcs-md.md)].cs 檔案。  
  
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
 預設的動詞命令是使用者按兩下 Windows 檔案總管中的檔案時所執行的動作。 預設的動詞命令為動詞命令指定為預設值的 HKEY_CLASSES_ROOT\\*progid*\Shell 索引鍵。 如果未不指定任何值，預設的動詞命令是指定 HKEY_CLASSES_ROOT 裡的第一個指令動詞\\*progid*\Shell 索引鍵清單。  
  
> [!NOTE]
>  如果您想要變更預設的並排顯示部署中的延伸模組的動詞命令，請考慮對安裝與移除的影響。 在安裝期間會覆寫原始的預設值。  
  
## <a name="see-also"></a>另請參閱  
 [管理並存的檔案關聯](../extensibility/managing-side-by-side-file-associations.md)
