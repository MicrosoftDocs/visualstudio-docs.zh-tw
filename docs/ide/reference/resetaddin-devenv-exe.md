---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 36b003f4890b16a7b69f7f66f8b0ef83a0ade7ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
移除與所指定增益集相關聯的命令和命令 UI。  
  
## <a name="syntax"></a>語法  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>引數  
 `AddIn`  
 選擇性。 增益集的命令名稱。  
  
## <a name="remarks"></a>備註  
 根據預設，增益集的命令名稱等於 \<增益集方案名稱>.Connect.\<增益集方案名稱>，並出現在 Connect.cs 中作為 `Exec` 方法的 `commandName` 參數。 您也可以確認命令名稱，方法是在 Visual Studio 的 [命令] 視窗中開始輸入增益集名稱，並使用 Intellisense 填入其餘部分。  
  
## <a name="example"></a>範例  
 下列範例會啟動 Visual Studio，並防止在啟動時執行 `MyAddin` 增益集。  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>請參閱  
 [將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)   
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)