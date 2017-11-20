---
title: "如何： 指定使用者將從安裝的位置 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 41a601febff80b002512a3783d8405dc42e5d766
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>如何：指定位置讓終端使用者從此處執行安裝作業
發行時[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式中，若要下載並安裝應用程式使用者的去向不一定是一開始發行應用程式的位置。 例如，在某些組織中開發人員可能會發行臨時伺服器，應用程式，然後系統管理員，將移至 Web 伺服器應用程式。  
  
 在此情況下，您可以使用`Installation URL`屬性來指定使用者將會前往下載應用程式的 Web 伺服器。 這是必要的如此應用程式資訊清單可得知何處尋找更新。  
  
 `Installation URL`屬性可以設定上**發行**頁面**專案設計工具**。  
  
 **請注意**`Installation URL`屬性也可以設定使用**PublishWizard**。 如需詳細資訊，請參閱[如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
### <a name="to-specify-an-installation-url"></a>若要指定安裝 URL  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  在安裝 URL 欄位中，輸入使用完整的 URL 格式 http://www.microsoft.com/ApplicationName 或使用格式的 UNC 路徑所使用的安裝位置\\\Server\ApplicationName。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 指定 Visual Studio 複製檔案的位置](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)