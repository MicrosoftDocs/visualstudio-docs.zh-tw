---
title: 錯誤： 非驗證防火牆 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: dda1acb8-bed7-4bc8-9991-9cdc49c2ac1e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8907dac5310e2f70ff5a7053cc564e72b0b2cd98
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186039"
---
# <a name="error-firewall-no-authentication"></a>錯誤：非驗證防火牆
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

遠端機器上的網際網路連線防火牆並未設定允許遠端偵錯。 針對使用 `No Authentication` 的遠端偵錯，msvsmon.exe 必須加入至例外狀況清單。 可能也必須開啟某些 IPSEC 通訊埠。  
  
> [!NOTE]
>  遠端偵錯工具可以自動設定 Windows 防火牆。 當使用 Windows 防火牆以外的防火牆 (例如，協力廠商軟體防火牆或硬體防火牆) 時，必須手動設定防火牆允許遠端偵錯。 若要執行這項操作，請允許 msvsmon.exe 接聽所在的 TCP/IP 通訊埠上的流量。 根據預設，這些通訊埠為 4018 和 4019，其中 4018 會在所有作業系統上使用，而 4019 僅在 Windows x64 上用來允許對 x86 處理序進行偵錯。  
  
 如需詳細資訊，請參閱 <<c0> [ 設定 Up the Remote Tools 在裝置上](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)。



