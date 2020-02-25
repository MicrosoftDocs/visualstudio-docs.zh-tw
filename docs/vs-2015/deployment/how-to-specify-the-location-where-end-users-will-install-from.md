---
title: 如何：指定將從中安裝終端使用者的位置 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82181d906adc3454dfe77ef4fb21d8bdf99df16f
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557981"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>如何：指定位置讓終端使用者從此處執行安裝作業
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

發行 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式時，使用者移至下載和安裝應用程式的位置不一定是您最初發行應用程式的位置。 例如，在某些組織中，開發人員可能會將應用程式發行至預備伺服器，然後系統管理員會將應用程式移至 Web 服務器。  
  
 在此情況下，您可以使用 [`Installation URL`] 屬性來指定使用者將在其中下載應用程式的網頁伺服器。 這是必要的，讓應用程式資訊清單知道要尋找更新的位置。  
  
 您可以在 [**專案設計**工具] 的 [**發行**] 頁面上設定 [`Installation URL`] 屬性。  
  
 **注意**`Installation URL` 屬性也可以使用**發行精靈**來設定。 如需詳細資訊，請參閱[如何：使用發行嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
### <a name="to-specify-an-installation-url"></a>若要指定安裝 URL  
  
1. 在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。  
  
2. 按一下 [Publish (發行)] 索引標籤。  
  
3. 在 [安裝 URL] 欄位中，使用 `https://www.contoso.com/ApplicationName`格式的完整 URL，或使用 `\\Server\ApplicationName`格式的 UNC 路徑，輸入安裝位置。  
  
## <a name="see-also"></a>另請參閱  
 [如何：指定 Visual Studio 複製檔案的位置](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
