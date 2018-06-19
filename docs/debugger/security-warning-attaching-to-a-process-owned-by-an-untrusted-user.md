---
title: 安全性警告： 將附加至不受信任的使用者所擁有的處理序可能十分危險。 如果下列資訊看起來有問題，或您不確定，不會附加至這個處理序 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68d88e01dde07789467272db830cae45ca5d60c4
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
ms.locfileid: "34178004"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>安全性警告： 將附加至不受信任的使用者所擁有的處理序可能十分危險。 如果下列資訊看起來有問題，或您不確定，不會附加至這個處理序
當您附加至包含部分受信任程式碼的處理序，或是附加至在附加之前即由未受信任之使用者所擁有的處理序時，這個警告對話方塊就會出現。 包含惡意程式碼的未受信任處理序可能會損害進行偵錯的電腦。 如果您有理由不信任此程序，則您應該按一下**取消**避免進行偵錯。  
  
 偵錯合法的案例時，請隱藏這個警告，關閉 Visual Studio，並將此登錄機碼值為 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`，然後重新啟動 Visual Studio。 在您完成情節的偵錯之後，將值重設為 0，並重新啟動 Visual Studio。  
  
 「受信任的使用者」包括您自己以及一組標準使用者，這些使用者通常是在已安裝 .NET Framework 的電腦上定義，例如 `aspnet`、`localsystem`、`networkservice` 和 `localservice`。  
  
## <a name="uielement-list"></a>UIElement 清單  
 名稱  
 要求進行偵錯的組件名稱  
  
 使用者  
 目前使用者  
  
 附加  
 按下以藉由附加繼續偵錯  
  
 不附加  
 不附加至處理序  
  
## <a name="see-also"></a>另請參閱  
 [附加至執行中處理程序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)