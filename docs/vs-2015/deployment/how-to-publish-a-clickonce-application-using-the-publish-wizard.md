---
title: 如何： 發行 ClickOnce 應用程式使用發行精靈 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 82600212626ea5c5f0543579b82d95903f1fcc8e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293900"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>如何：使用發行精靈發行 ClickOnce 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要讓使用者可以使用 ClickOnce 應用程式，您必須將它發行至檔案共用或路徑、FTP 伺服器或卸除式媒體。 您可以使用 [發行精靈]，發行應用程式與發佈相關的其他屬性位於**發佈**頁**專案設計工具**。 如需詳細資訊，請參閱 <<c0> [ 發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)。  
  
 在執行 [發行精靈] 之前，您應該適當設定發行屬性。 例如，如果您想要將指定的金鑰來簽署 ClickOnce 應用程式，您可以等**Signing**頁**專案設計工具**。 如需詳細資訊，請參閱[保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)。  
  
> [!NOTE]
>  當您使用 ClickOnce 安裝多個版本的應用程式時，安裝會將舊版應用程式移至您指定之發行位置中名為 Archive 的資料夾。 以這種方式封存先前的版本可將安裝目錄與舊版的資料夾分開。  
  
> [!NOTE]
>  根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。 若要變更設定，請在 [工具]  功能表上按一下 [匯入和匯出設定]  。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-publish-to-a-file-share-or-path"></a>發行至檔案共用或路徑  
  
1.  在 **方案總管 中**，選取 應用程式專案。  
  
2.  在 **建置**功能表上，按一下**發佈**`Projectname`。  
  
     [發行精靈] 隨即出現。  
  
3.  在 [**您要在其中發行應用程式？** 頁面上，輸入有效的 FTP 伺服器位址或使用其中一種格式顯示，有效的檔案路徑，然後按一下**下一步]**。  
  
4.  在 **使用者要如何安裝應用程式？** 頁面上，選取使用者要前往安裝應用程式的位置：  
  
    -   如果使用者將從網站安裝，請按一下**從網站**並輸入 URL 對應至輸入上一個步驟中的檔案路徑。 按 [ **下一步**]。 (當您指定 FTP 位址做為發行位置時，通常會使用這個選項。 不支援直接從 FTP 下載。 因此，您必須在此輸入 URL。)  
  
    -   如果使用者將安裝應用程式，直接從檔案共用，請按一下**從 UNC 路徑或檔案共用**，然後按一下**下一步**。 (這是用來發行位置的表單 c:\deploy\myapp 或\\\server\myapp。)  
  
    -   如果使用者將從抽取式媒體安裝，請按一下**從 CD-ROM 或 DVD-ROM**，然後按一下**下一步**。  
  
5.  在 **應用程式可離線？** 頁面上，按一下適當的選項：  
  
    -   如果您想要讓應用程式執行時使用者會與網路中斷連線，請按一下**可以，此應用程式將可以使用線上或離線**。 在快顯**啟動**功能表將會建立應用程式。  
  
    -   如果您想要從發行位置直接執行應用程式，按一下**否，此應用程式才可使用線上**。 在快顯**啟動**功能表將不會建立。  
  
     按 [下一步]  以繼續。  
  
6.  按一下 **完成**發行應用程式。  
  
     發行狀態會隨即顯示在狀態通知區域中。  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>發行至 CD-ROM 或 DVD-ROM  
  
1.  在 **方案總管**，以滑鼠右鍵按一下 應用程式專案，然後按一下**屬性**。  
  
     [專案設計工具] 隨即出現。  
  
2.  按一下**發行**索引標籤以開啟**發行**頁面**專案設計工具**，然後按一下**發行精靈**按鈕。  
  
     [發行精靈] 隨即出現。  
  
3.  在 **您要在其中發行應用程式？** 頁面上，輸入檔案路徑或 FTP 位置，會發行應用程式，例如 d:\deploy。 然後按一下**下一步**以繼續。  
  
4.  在 **使用者要如何安裝應用程式？** 頁面上，按一下 從**CD-ROM 或 DVD-ROM**，然後按一下**下一步**。  
  
    > [!NOTE]
    >  如果您想要自動執行安裝時在 CD-ROM 插入磁碟機中，開啟**發佈**頁面**專案設計工具**然後按一下**選項**按鈕，然後在**發行選項**精靈中，選取**若是使用光碟安裝時自動啟動安裝程式插入光碟後**。  
  
5.  如果您使用 CD-ROM 散發應用程式，可能會想要從網站提供更新。 在 **哪裡將應用程式檢查更新檔？** 頁面上，選擇 更新 選項：  
  
    -   如果應用程式會檢查更新，請按一下**應用程式會檢查從下列位置更新**，輸入將會張貼更新的位置。 這可以是檔案位置、網站或 FTP 伺服器。  
  
    -   如果應用程式將不會檢查更新，請按一下**應用程式將不會檢查更新**。  
  
     按 [下一步]  以繼續。  
  
6.  按一下 **完成**發行應用程式。  
  
     發行狀態會隨即顯示在狀態通知區域中。  
  
    > [!NOTE]
    >  在發行完成後，您必須使用 CD 燒錄機或 DVD 燒錄機，將檔案從步驟 3 中指定的位置複製到 CD-ROM 或 DVD-ROM 媒體。  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [使用 ClickOnce 部署 Office 方案](http://msdn.microsoft.com/library/feb516b3-5e4d-449a-9fd2-347d08d90252)



