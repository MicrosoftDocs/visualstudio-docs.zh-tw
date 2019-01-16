---
title: 64 位元應用程式的部署必要條件 |Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86d7512101adf58f13a07481910ab1c28251b8da
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885247"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>部署 64 位元應用程式的必要條件
ClickOnce 部署支援在 64 位元平台上的應用程式的安裝。 目標平台包括 **x86** (表示 32 位元平台)、**x64** (表示支援 AMD64 和 EM64T 指令集的電腦)，以及 **Itanium** (表示 64 位元 Itanium 處理器)。  

## <a name="prerequisites"></a>必要條件  
 下表列出一些可轉散發套件，您可以將它們當做 64 位元應用程式安裝的必要條件來使用。  

 如果您選取沒有 64 位元元件的必要條件，可能會出現警告，指出選取的套件不適用於 64 位元平台。  


| 可轉散發套件 | x64 支援 | IA64 支援 |
| - |-------------|--------------|
| [!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)] | 是 | 否 |
| Visual C++ 2010 執行階段程式庫 (IA64) | 否 | 是 |
| Visual C++ 2010 執行階段程式庫 (x64) | 是 | 否 |
| Microsoft .NET Framework 4 (x86 和 x64) | 是 | |
| Microsoft .NET Framework 4 Client Profile (x86 和 x64) | 是 | |

## <a name="see-also"></a>另請參閱  
 [部署應用程式、 服務和元件](../deployment/deploying-applications-services-and-components.md)   
 [如何：隨著 ClickOnce 應用程式安裝必要軟體](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64 位元應用程式](/dotnet/framework/64-bit-apps)