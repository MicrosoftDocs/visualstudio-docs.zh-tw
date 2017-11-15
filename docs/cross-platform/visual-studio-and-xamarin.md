---
title: "Visual Studio 和 Xamarin | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: e84f946915328eb0ee5a49e690b2ee520d29e968
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio 和 Xamarin
Xamarin 是行動應用程式開發平台，可從通用 C#/.NET 程式碼基底建置原生 iOS、Android 和 Windows 應用程式，以在平台之間重複使用 75% 到將近 100% 的程式碼。 使用 Xamarin 和 C# 撰寫的應用程式可完整存取基礎平台 API，而且能夠建置原生使用者介面，並編譯為平台專用的封裝，因此不會對執行階段效能造成太大的影響。 (注意︰Xamarin 也支援 F#，但本文將只著重在 C#。 目前不支援 Visual Basic。)  
  
 更棒的是，熟悉 C#、.NET 和 Visual Studio 的開發人員在使用 Xamarin 開發行動應用程式時，不需要了解 Objective-C 或 Java 等機器碼語言，也能享有相同的功能和產能，包括在 Android、iOS 和 Windows 裝置上進行遠端偵錯。 因此，許多具有美觀使用者介面的高效能應用程式 (例如 NASCAR、Aviva 和 MixRadio) 意料之中都是使用 Xamarin 所建置。  
  
 本文可協助您評估 **Visual Studio 搭配 Xamarin**的完整功能以建置這些經驗。  
  
-   開始進行[設定和安裝](../cross-platform/setup-and-install.md)，此程序會花費一些時間 (通常是 2-4 小時，取決於您的網際網路連線速度、已安裝的項目及選取的選項)。  
  
-   執行安裝程式時，您可以[了解 Xamarin 的行動裝置開發](../cross-platform/learn-about-mobile-development-with-xamarin.md)，您將能在其中了解 Xamarin 的本質、比較 Xamarin.Forms 與原生 UI，以及更多資訊。  
  
-   安裝完成之後，[驗證您的 Xamarin 環境](../cross-platform/verify-your-xamarin-environment.md)。  
  
-   藉由逐步執行[了解在 Visual Studio 中建置 Xamarin.Forms 應用程式的基本概念](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)教學課程來完成。  
  
 您可以透過[任何版本的 Visual Studio 2015](https://www.visualstudio.com/vs-2015-product-editions) (Community、Professional 及 Enterprise) 來使用所有的 Xamarin 功能。 另請注意，截至 2016 年 3 月 31 日，Xamarin 已隨附於所有版本的 Visual Studio 2015 中，不再需要個別授權。 針對 Visual Studio 2013，您可以個別安裝 Xamarin，如[設定和安裝](../cross-platform/setup-and-install.md)主題中所述。  
  
> [!NOTE]
>  這些指示會說明最簡單且最直接的電腦設定，適用於具有 Windows 和 Visual Studio 背景的人員。 在這項設定中，整體開發經驗已經過簡化，因為您只有在使用 iOS 模擬器和行動網卡時才需要與 Mac 互動。 如果您具備 Mac 背景，則建議您在 Parallels/VMWare 中執行 Visual Studio，或是使用 Xamarin Studio Community。 如需相關指示，請參閱[針對 Mac 使用者的設定、安裝和驗證](../cross-platform/setup-install-and-verifications-for-mac-users.md)。  
  
> [!NOTE]
>  如果您想要尋求以 HTML 和 CSS 為基礎的跨平台開發解決方案，請試試 Visual Studio Tools for Apache Cordova，如 [Visual Studio 中的跨平台開發](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML)所述。