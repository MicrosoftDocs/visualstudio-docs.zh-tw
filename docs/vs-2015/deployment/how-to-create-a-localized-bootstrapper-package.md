---
title: 如何：建立當地語系化的啟動載入器套件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ec3cd1365826c1a06b2d0f7bd6da377c8dc4d46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839241"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>如何：建立當地語系化啟動載入器套件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

建立啟動載入器套件之後，您可以為每一個地區設定建立另外兩個檔案，藉此建立當地語系化版本的啟動載入器套件：軟體授權合約檔案 (例如 eula.rtf) 和套件資訊清單 (package.xml)。  
  
 根據預設，Visual Studio 2010 只包含 .NET Framework 4、.NET Framework 4 Client Profile、F# Runtime 2.0 和 F# Runtime 4.0 的當地語系化啟動載入器套件。 您只要完成三個步驟，就能為其他啟動載入器建立當地語系化套件。  
  
1. 建立以 \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages BootstrapperPackageName 中的地區設定名稱命名的資料夾 \\ * *。  
  
2. 建立包含啟動載入器套件之軟體授權合約的檔案，然後放入新資料夾中。  
  
3. 建立名為 package.xml 的套件資訊清單，更新字串和文化特性，然後將檔案放入新資料夾中。 如果您已建立目標語言的 Visual Studio 啟動載入器，可以複製 Visual Studio package.xml 檔，並且在這個步驟中進行修改。  
  
> [!NOTE]
> 如果您使用安裝專案部署應用程式，可以藉由變更 **Localization** 屬性將應用程式當地語系化。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>建立當地語系化的啟動載入器套件  
  
1. 以地區設定名稱建立資料夾。  
  
     在32位的電腦上，于 \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ *BootstrapperPackageName*\ 資料夾中建立資料夾。  
  
     在64位的電腦上，于 \Program 檔案中建立資料夾 (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ *BootstrapperPackageName*\ 資料夾。  
  
     下表顯示可用來比對地區設定的資料夾名稱。  
  
    |地區設定|資料夾名稱|  
    |------------|-----------------|  
    |簡體中文|zh-Hans|  
    |繁體中文|zh-Hant|  
    |捷克文|cs|  
    |德文|de|  
    |英文|en|  
    |西班牙文|es|  
    |法文|fr|  
    |義大利文|it|  
    |韓文|ko|  
    |日文|ja|  
    |波蘭文|pl|  
    |葡萄牙文 (巴西)|pt-BR|  
    |俄文|ru|  
    |土耳其文|tr|  
  
2. 建立包含啟動載入器套件之軟體授權合約的檔案，然後放入新資料夾中。  
  
3. 建立名為 package.xml 的套件資訊清單，然後放入新資料夾中。 如需詳細資訊，請參閱 [如何：建立封裝資訊清單](../deployment/how-to-create-a-package-manifest.md)。  
  
4. 更新套件資訊清單的 `<Strings>` 區段，讓字串能夠以正確的地區設定語言顯示。  
  
5. 變更 `<String Name="Culture">` 值，以符合資料夾名稱。  
  
6. 儲存 package.xml 檔。  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>為 .NET Framework 3.5 Service Pack 1 建立以法文當地語系化的啟動載入器套件  
  
1. 建立名為 fr 的資料夾。 資料夾名稱必須符合地區設定名稱。  
  
     在 32 位元電腦上，於 \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\ 資料夾中建立資料夾。  
  
     在 64 位元電腦上，於 \Program Files (86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\ 資料夾中建立資料夾。  
  
2. 將當地語系化版本的軟體授權合約放入 fr 資料夾中。  
  
3. 將 \Program Files (x86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml 檔複製到 fr 資料夾，然後在 XML 設計工具中開啟檔案。  
  
4. 更新套件資訊清單的 `<Strings>` 區段，讓錯誤字串以法文顯示。  
  
5. 將 `<String Name="Culture">` 值變更為 fr。  
  
6. 儲存 package.xml 檔。  
  
## <a name="see-also"></a>另請參閱  
 [建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)   
 [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)   
 [如何：建立封裝資訊清單](../deployment/how-to-create-a-package-manifest.md)
