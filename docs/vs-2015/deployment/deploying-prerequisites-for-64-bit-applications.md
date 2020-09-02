---
title: 部署64位應用程式的必要條件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 92f30e8e059475c907da184aa59a8e4b7a2cf19f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675575"
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>64 位元應用程式的部署必要條件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce 部署支援在 64 位元平台上的應用程式的安裝。 目標平台包括 **x86** (表示 32 位元平台)、**x64** (表示支援 AMD64 和 EM64T 指令集的電腦)，以及 **Itanium** (表示 64 位元 Itanium 處理器)。  
  
## <a name="prerequisites"></a>先決條件  
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
 [64位應用程式](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)
