---
title: 64 位元應用程式的部署必要條件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 0f98a611b382f3884ede2e1e239944b9e584ab77
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489659"
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>64 位元應用程式的部署必要條件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[64 位元應用程式的部署必要條件](https://docs.microsoft.com/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications)。  
  
ClickOnce 部署支援在 64 位元平台上的應用程式的安裝。 目標平台包括**x86**對於 32 位元平台， **x64**機器支援 AMD64 和 EM64T 指令集，並**Itanium** 64 位元 Itanium 處理器。  
  
## <a name="prerequisites"></a>必要條件  
 下表列出一些可轉散發套件，您可以將它們當做 64 位元應用程式安裝的必要條件來使用。  
  
 如果您選取沒有 64 位元元件的必要條件，可能會出現警告，指出選取的套件不適用於 64 位元平台。  
  
|可轉散發套件|x64 支援|IA64 支援|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../includes/vsto-runtime-md.md)]|是|否|  
|Visual C++ 2010 執行階段程式庫 (IA64)|否|是|  
|Visual C++ 2010 執行階段程式庫 (x64)|是|否|  
|Microsoft .NET Framework 4 (x86 和 x64)|是||  
|Microsoft .NET Framework 4 Client Profile (x86 和 x64)|是||  
  
## <a name="see-also"></a>另請參閱  
 [部署應用程式、服務和元件](../deployment/deploying-applications-services-and-components.md)   
 [如何：使用 ClickOnce 應用程式安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64 位元應用程式](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)



