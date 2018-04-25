---
title: Visual Studio 和 Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: c16898fa94bcdb051b215f3ff89cf4d42cbe7fe7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio 和 Xamarin

Xamarin 是適用於從通用 C#/.NET 程式碼基底建置原生的 iOS、Android 和 Windows 應用程式的行動應用程式開發平台。 使用 Xamarin 所撰寫的應用程式可以在平台之間達到 75% 至將近 100% 的程式碼重複使。 這些應用程式可以完整存取基底平台 API，並整合原生的使用者介面。 它們會編譯為平台特定的套件，且對執行階段效能影響不大。 (注意︰Xamarin 也支援 F#，但本文將只著重在 C#。 目前不支援 Visual Basic。)  
  
熟悉 C#、NET 和 Visual Studio 的開發人員在使用適用於行動應用程式的 Xamarin 時，會享有相同的功能和生產力。 這些優點包括在 Android、iOS 和 Windows 裝置上進行遠端偵錯，而不需要了解 Objective-C 或 Java 等原生程式設計語言。 因此，許多具有美觀使用者介面的高效能應用程式 (例如 NASCAR、Aviva 和 MixRadio) 意料之中都是使用 Xamarin 所建置。  
  
本文可協助您評估 **Visual Studio 搭配 Xamarin** 的完整功能以建置這些經驗。  
  
-   從 [Setup and install](../cross-platform/setup-and-install.md)開始，此程序會花費一些時間 (通常是 2-4 小時，取決於您的網際網路連線速度、已安裝的項目及選取的選項)。  
  
-   執行安裝程式時，您可以[了解 Xamarin 的行動裝置開發](learn-about-mobile-development-with-xamarin.md)，您將能在其中了解 Xamarin 的本質、比較 Xamarin.Forms 與原生 UI，以及更多資訊。  
  
-   安裝完成之後，[驗證您的 Xamarin 環境](../cross-platform/verify-your-xamarin-environment.md)。  
  
-   藉由逐步執行[了解在 Visual Studio 中建置 Xamarin.Forms 應用程式的基本概念](/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)教學課程來完成。  
  
您可以透過[任何版本的 Visual Studio 2017](https://www.visualstudio.com/vs) (Community、Professional 及 Enterprise) 來使用所有的 Xamarin 功能。 不需要個別的授權。  
  
> [!NOTE]
>  這些指示會說明最簡單且最直接的電腦設定，適用於具有 Windows 和 Visual Studio 背景的開發人員。 在這項設定中，整體開發經驗已經過簡化，因為您只有在使用 iOS 模擬器和行動網卡時才需要與 Mac 互動。 另一方面，如果您來自 Mac 背景，我們建議您在 Parallels 或 VMWare 中執行 Visual Studio，或者使用 Visual Studio for Mac。 如需相關指示，請參閱[針對 Mac 使用者的設定、安裝和驗證](../cross-platform/setup-install-and-verifications-for-mac-users.md)。  
  
> [!NOTE]
>  如果您想要尋求以 HTML 和 CSS 為基礎的跨平台開發解決方案，請試試 Visual Studio Tools for Apache Cordova，如 [Visual Studio 中的跨平台開發](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML)所述。