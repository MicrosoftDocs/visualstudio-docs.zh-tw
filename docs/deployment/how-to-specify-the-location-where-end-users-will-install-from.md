---
title: HOW TO：指定使用者將從安裝的位置 |Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e21938ed03a7bc8c03b910ce1c9bce7187f31255
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020681"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>HOW TO：指定位置讓終端使用者從此處執行安裝作業
發佈時[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式，下載並安裝應用程式使用者的位置不一定是一開始發行應用程式的位置。 例如，在某些組織中開發人員可能會發行至預備伺服器，應用程式，然後以系統管理員會移至 Web 伺服器應用程式。  
  
 在此情況下，您可以使用`Installation URL`屬性來指定使用者要前往下載應用程式的 Web 伺服器。 這是必要的因此，應用程式資訊清單會知道要尋找更新。  
  
 `Installation URL`上設定屬性**發佈**頁面**專案設計工具**。  
  
 **附註**`Installation URL`屬性也可以設定使用**發行精靈**。 如需詳細資訊，請參閱[＜How to：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
### <a name="to-specify-an-installation-url"></a>若要指定安裝 URL  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [發佈] 索引標籤。  
  
3.  在 安裝 URL 欄位中，輸入 使用完整的 URL，使用格式的安裝位置*http://www.microsoft.com/ApplicationName*，或使用的格式將 UNC 路徑 *\\\Server\ApplicationName*.  
  
## <a name="see-also"></a>另請參閱  
 [如何：指定 Visual Studio 複製檔案的位置](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用 [發佈精靈] 發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)