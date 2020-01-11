---
title: 錯誤：請確認目的電腦上的 DNS 設定是否正確 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35c258a018bec8bd38f8b43690c18b37ee9d6c39
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851939"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>錯誤：請確認目標電腦上的 DNS 設定都正確
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可能會在嘗試進行遠端偵錯時，得到下列錯誤訊息：  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 當目標電腦無法解析 Visual Studio 偵錯工具主機電腦的名稱時，便會發生這個錯誤。 請檢查目標電腦上的 DNS 設定。  
  
- 如需檢視在 Windows 8.1、Vista、Windows 7、Windows Server 2012、Windows Server 2008 或 Windows Server 2008 R2 上 DNS 的設定資訊，請執行下列作業：在 [開始] 功能表上，選擇 [說明及支援]，然後搜尋 [變更 TCP/IP] 設定。  
  
- 如需詳細資訊，請移至[Microsoft Windows 網站](https://windows.microsoft.com/)並搜尋**變更 tcp/ip 設定**。  
  
  如果無法解決 DNS 問題，您可以嘗試用其他帳戶執行 [遠端偵錯工具]。 只有在您使用本機系統或網路服務帳戶執行 [遠端偵錯工具] 時，才會發生這個錯誤。 如果是以其他帳戶執行 [遠端偵錯工具]，就可以使用不需要 DNS 的 NTLM 驗證。 。 如需相關程式，請參閱[錯誤：目的電腦上的 Visual Studio 遠端偵錯工具服務無法連回這部電腦](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)。
