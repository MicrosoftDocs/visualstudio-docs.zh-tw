---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6321433b506d41df57150b5a135a800a16cef0ab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689673"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 [在 Visual Studio 中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
