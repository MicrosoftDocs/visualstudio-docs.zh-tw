---
title: RC 工作 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ff118a6d32a182d1060cc051f24352b16037039
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "47588777"
---
# <a name="rc-task"></a>RC 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[RC 工作](https://docs.microsoft.com/visualstudio/msbuild/rc-task)。  
  
  
包裝 Microsoft Windows 資源編譯器工具 (rc.exe)。 **RC** 工作會將資料指標、圖示、點陣圖、對話方塊和字型這類資源編譯為資源 (.res) 檔案。 如需詳細資訊，請參閱 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 網站上的＜資源編譯器＞。  
  
## <a name="parameters"></a>參數  
 下表描述 RCtask 的參數。 大部分的工作參數以及數組參數會對應到命令列選項。  
  
|參數|描述|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|選擇性的 **String[]** 參數。<br /><br /> 將目錄加入至要搜尋 include 檔案的目錄清單。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC (RC 命令列)](http://go.microsoft.com/fwlink/?LinkId=155730) 中的 **/I** 選項。|  
|**AdditionalOptions**|選擇性的 **String** 參數。<br /><br /> 命令列 optionsor 範例清單：**"**_/option1 /option2 /option#_"。 使用此參數，來指定任何其他 **RC** 工作參數未表示的命令列選項。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC (RC 命令列)](http://go.microsoft.com/fwlink/?LinkId=155730) 中的選項。|  
|**文化特性**|選擇性的 **String** 參數。<br /><br /> 指定代表資源中所使用文化特性 (Culture) 的地區設定識別碼。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC (RC 命令列)](http://go.microsoft.com/fwlink/?LinkId=155730) 中的 **/l** 選項。|  
|**IgnoreStandardIncludePath**|選擇性的 **Boolean** 參數。<br /><br /> 如果 `true`，可防止資源編譯器在搜尋標題檔或資源檔時檢查 INCLUDE 環境變數。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC (RC 命令列)](http://go.microsoft.com/fwlink/?LinkId=155730) 中的 **/x** 選項。|  
|**NullTerminateStrings**|選擇性的 **Boolean** 參數。<br /><br /> 如果 `true`，null 會終止字串資料表中的所有字串。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC (RC 命令列)](http://go.microsoft.com/fwlink/?LinkId=155730) 中的 **/n** 選項。|  
|**PreprocessorDefinitions**|選擇性的 **String[]** 參數。<br /><br /> 定義資源編譯器的一或多個前置處理器符號。 指定巨集符號清單。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC (RC 命令列)](http://go.microsoft.com/fwlink/?LinkId=155730) 中的 **/d** 選項。 另請參閱此表格中的 **UndefinePreprocessorDefinitions**。|  
|**ResourceOutputFileName**|選擇性的 **String** 參數。<br /><br /> 指定資源檔的名稱。 指定資源檔名稱。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC (RC 命令列)](http://go.microsoft.com/fwlink/?LinkId=155730) 中的 **/fo** 選項。|  
|**ShowProgress**|選擇性的 **Boolean** 參數。<br /><br /> 如果 `true`，則會顯示報告編譯器進度的訊息。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC (RC 命令列)](http://go.microsoft.com/fwlink/?LinkId=155730) 中的 **/v** 選項。|  
|**來源**|必要的 `ITaskItem[]` 參數。<br /><br /> 定義工作可以耗用和發出的 MSBuild 來源檔案項目的陣列。|  
|**SuppressStartupBanner**|選擇性的 **Boolean** 參數。<br /><br /> 如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。<br /><br /> 如需詳細資訊，請鍵入 **/?** 命令列選項，然後參閱 **/nologo** 選項。|  
|**TrackerLogDirectory**|選擇性的 **String** 參數。<br /><br /> 指定追蹤器記錄目錄。|  
|**UndefinePreprocessorDefinitions**|取消定義前置處理器符號。<br /><br /> 如需詳細資訊，請參閱 MSDN 網站上[使用 RC (RC 命令列)](http://go.microsoft.com/fwlink/?LinkId=155730) 中的 **/u** 選項。 另請參閱此表格中的 **PreprocessorDefinitions**。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)



