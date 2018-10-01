---
title: 如何： 指定使用者將從安裝的位置 |Microsoft Docs
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
manager: wpickett
ms.openlocfilehash: 68f50fe847d1432292491cd2970c7897eb1388da
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497207"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>如何：指定位置讓終端使用者從此處執行安裝作業
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 指定位置所在的終端使用者會安裝從](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-the-location-where-end-users-will-install-from)。  
  
發佈時[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式，下載並安裝應用程式使用者的位置不一定是一開始發行應用程式的位置。 例如，在某些組織中開發人員可能會發行至預備伺服器，應用程式，然後以系統管理員會移至 Web 伺服器應用程式。  
  
 在此情況下，您可以使用`Installation URL`屬性來指定使用者要前往下載應用程式的 Web 伺服器。 這是必要的因此，應用程式資訊清單會知道要尋找更新。  
  
 `Installation URL`上設定屬性**發佈**頁面**專案設計工具**。  
  
 **附註**`Installation URL`屬性也可以設定使用**發行精靈**。 如需詳細資訊，請參閱 <<c0> [ 如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
### <a name="to-specify-an-installation-url"></a>若要指定安裝 URL  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [**發佈**] 索引標籤。  
  
3.  在 安裝 URL 欄位中，輸入 使用完整的 URL，使用格式的安裝位置 http://www.microsoft.com/ApplicationName，或使用的格式將 UNC 路徑\\\Server\ApplicationName。  
  
## <a name="see-also"></a>另請參閱  
 [如何：指定 Visual Studio 複製檔案的位置](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



