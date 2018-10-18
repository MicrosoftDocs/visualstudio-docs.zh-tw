---
title: 錯誤： 在本機電腦上的防火牆 |Microsoft Docs
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
- vs.debug.error.firewall.localmachine
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cbca2e944e7313e54fd469dd41774f40931ee3d2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245345"
---
# <a name="error-firewall-on-local-machine"></a>錯誤：本機電腦的防火牆
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本機電腦 (也就是執行 Visual Studio 的電腦) 上的網際網路連線防火牆，並未設定允許遠端偵錯。 針對使用預設傳輸的 Managed 或機器碼遠端偵錯，您必須為 DCOM 傳輸開啟 TCP 135 通訊埠。 您必須開啟檔案和印表機共用，並且必須將 devenv.exe 加入例外狀況清單。 可能也必須開啟某些 IPSEC 通訊埠。  
  
 如需詳細資訊，請參閱 <<c0> [ 設定 Up the Remote Tools 在裝置上](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)。



