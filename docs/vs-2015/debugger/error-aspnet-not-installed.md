---
title: 錯誤： 尚未安裝 ASP.NET |Microsoft Docs
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
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20a6d85fbdc7fad9077a19704b6c448c73dae787
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739598"
---
# <a name="error-aspnet-not-installed"></a>錯誤：尚未安裝 ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您嘗試偵錯的電腦尚未正確安裝 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 時，就會發生這個錯誤。 這可能表示從未安裝 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]，或是先安裝 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 之後才安裝 IIS。  
  
### <a name="to-reinstall-aspnet"></a>若要重新安裝 ASP.NET  
  
1.  從 [命令提示字元] 視窗，執行下列命令：  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     何處*版本*代表安裝在您的電腦，例如 v1.0.370 上的.NET framework 的版本號碼。 您可以判斷的 framework 版本尋找`\WINDOWS\Microsoft.NET\Framework`目錄。  
  
    > [!NOTE]
    >  您可以安裝 Windows Server 2003、windows[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]利用**新增或移除程式**控制項台中。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



