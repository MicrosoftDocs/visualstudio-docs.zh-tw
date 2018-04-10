---
title: 如何： 管理 ClickOnce 應用程式的更新 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: f239f13a7dcefe0ce6f2bf8c12c641e97a48ce26
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>如何：管理 ClickOnce 應用程式中的更新
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可以自動或以程式設計方式檢查更新。 身為開發人員，您會有許多彈性，指定何時以及如何執行更新檢查、 是否強制、 更新和應用程式應該檢查更新。  
  
 您可以設定要在應用程式啟動後檢查更新自動在應用程式啟動之前，或在設定間隔的應用程式。 此外，您可以指定最小必要的版本。如果使用者的版本低於所需的版本，也就是已安裝更新。  
  
 您可以設定要檢查更新，以程式設計方式為基礎的事件，例如使用者要求的應用程式。 此程序 < 若要以程式設計方式檢查更新 」 本主題中的顯示方式，您可以撰寫程式碼乃使用<xref:System.Deployment.Application.ApplicationDeployment>根據事件的類別來檢查更新。  
  
 您也可以部署從一個位置的應用程式，並從另一個更新。 請參閱 < 若要指定不同的更新位置。 」 程序  
  
 如需詳細資訊，請參閱[選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)。  
  
 在管理更新行為的**應用程式更新**對話方塊中，可從**發行**頁面**專案設計工具。**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>若要在應用程式啟動前，先檢查更新  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**更新** 按鈕以開啟**應用程式更新** 對話方塊。  
  
4.  在**應用程式更新**對話方塊方塊中，請確定**應用程式應該檢查更新檔**選取核取方塊。  
  
5.  在**選擇應用程式應該於何時檢查更新**區段中，選取**應用程式啟動之前**。 這可確保永遠連線到網路的使用者執行應用程式，使用最新的更新。  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>若要檢查在背景中更新應用程式啟動後  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**更新** 按鈕以開啟**應用程式更新** 對話方塊。  
  
4.  在**應用程式更新**對話方塊方塊中，請確定核取方塊**應用程式應該檢查更新檔**已選取。  
  
5.  在**選擇應用程式應該於何時檢查更新 區段**，選取**應用程式啟動後**。 應用程式會啟動更快速地這種方式，然後將會在背景中，檢查更新，並只在有更新可用時通知使用者。 安裝之後，更新不會影響應用程式重新啟動之前。  
  
6.  在**指定應用程式應該要檢查更新的頻率**區段中，選取 **每次執行應用程式檢查**（預設值） 或**檢查每個**並輸入數字和時間間隔。  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>若要指定應用程式的最小必要的版本  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**更新** 按鈕以開啟**應用程式更新** 對話方塊。  
  
4.  在**應用程式更新**對話方塊方塊中，請確定**應用程式應該檢查更新檔**選取核取方塊。  
  
5.  選取**指定此應用程式的最小必要的版本**核取方塊，然後再輸入**主要**，**次要**，**建置**，和**修訂**應用程式的數字。  
  
### <a name="to-specify-a-different-update-location"></a>若要指定不同的更新位置  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**更新** 按鈕以開啟**應用程式更新** 對話方塊。  
  
4.  在**應用程式更新**對話方塊方塊中，請確定**應用程式應該檢查更新檔**選取核取方塊。  
  
5.  在**更新位置**欄位中，輸入具有完整的 URL，使用格式的更新位置http://Hostname/ApplicationName，或使用格式的 UNC 路徑\\\Server\ApplicationName 或按一下**瀏覽**按鈕來瀏覽的更新位置。  
  
### <a name="to-check-for-updates-programmatically"></a>若要以程式設計方式檢查更新  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**更新** 按鈕以開啟**應用程式更新** 對話方塊。  
  
4.  在**應用程式更新**對話方塊方塊中，請確定**應用程式應該檢查更新檔**核取方塊。 （或者，您可以選取此核取方塊，以檢查有更新，以程式設計的方式，也讓 ClickOnce 執行階段自動檢查更新。）  
  
5.  在**更新位置**欄位中，輸入具有完整的 URL，使用格式的更新位置http://Hostname/ApplicationName，或使用格式的 UNC 路徑\\\Server\ApplicationName 或按一下**瀏覽**按鈕來瀏覽的更新位置。 更新位置是應用程式將在其中尋找本身的更新版本。  
  
6.  建立使用者將會選取檢查更新的 Windows Form 上的按鈕、 功能表項目或其他使用者介面項目。 從該項目的事件處理常式，呼叫方法來檢查並安裝更新。 您可以找到這種方法在 Visual Basic 和 Visual C# 程式碼範例[How to： 檢查是否有應用程式更新以程式設計方式使用 ClickOnce 部署 API](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)。  
  
7.  建置您的應用程式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [應用程式更新對話方塊](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [如何：使用 ClickOnce 部署 API 以程式設計方式檢查應用程式更新](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)