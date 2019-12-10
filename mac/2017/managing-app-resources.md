---
title: 管理應用程式資源
description: 本文與說明如何在 Visual Studio for Mac 中為各種平台管理應用程式資源的多篇指南有關
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 61EAAB8F-3C32-4574-924F-CFC616604089
ms.openlocfilehash: c3572edc46d4f69a338ba655b32254126a7fce9c
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985283"
---
# <a name="managing-app-resources"></a>管理應用程式資源

應用程式資源檔案 (例如影像、文字檔案和音訊檔案) 是應用程式所需的項目，但不會與應用程式一起編譯。 Visual Studio for Mac 所支援的每個平台都會以不同的方式處理這些資源，如下列指南中所述：

## <a name="xamarinforms"></a>Xamarin.Forms

Xamarin.Forms 程式碼可在多個平台上執行；每個平台都有屬於自己的檔案系統，且每個檔案系統都會決定讀取和寫入檔案的方式。 在 Xamarin.Forms 中，您可以透過在每個平台上使用原生檔案 API，或是將檔案新增為內嵌資源，來管理應用程式資源。

* [使用影像](https://developer.xamarin.com/guides/xamarin-forms/user-interface/images/)
* [使用檔案]( https://developer.xamarin.com/guides/xamarin-forms/application-fundamentals/files/)

## <a name="xamarinios"></a>Xamarin.iOS

* [使用資源](https://developer.xamarin.com/guides/ios/application_fundamentals/working_with_resources/)
* [使用影像](https://developer.xamarin.com/guides/ios/application_fundamentals/working_with_images/)
* [使用檔案系統](https://developer.xamarin.com/guides/ios/application_fundamentals/working_with_the_file_system/)

## <a name="xamarinandroid"></a>Xamarin.Android

* [Android 資源](https://developer.xamarin.com/guides/android/application_fundamentals/resources_in_android/)

## <a name="xamarinmac"></a>Xamarin.Mac

* [使用影像](https://developer.xamarin.com/guides/mac/application_fundamentals/working-with-images/)

## <a name="see-also"></a>請參閱

- [管理應用程式資源 (Windows 上的 Visual Studio)](/visualstudio/ide/managing-application-resources-dotnet)