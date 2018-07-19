---
title: 如何： 指定 Visual Studio 複製檔案的位置 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b2a4d642bc551127f34fe7a64ec01665b7ace70
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078624"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>如何： 指定 Visual Studio 複製檔案的位置
當您使用 ClickOnce 發行應用程式時，`Publish Location`屬性會指定放置應用程式檔案和資訊清單的位置。 這可以是檔案路徑或 FTP 伺服器的路徑。  
  
 您可以指定`Publish Location`上的屬性**發佈**頁面**專案設計工具**，或使用 [發行精靈]。 如需詳細資訊，請參閱 <<c0> [ 如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
> [!NOTE]
>  當您使用 ClickOnce 安裝多個版本的應用程式時，安裝會將舊版應用程式移至您指定之發行位置中名為 Archive 的資料夾。 以這種方式封存先前的版本可將安裝目錄與舊版的資料夾分開。  
  
### <a name="to-specify-a-publishing-location"></a>指定發行位置  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下 [**發佈**] 索引標籤。  
  
3.  在 **發行位置**欄位中，輸入發行位置，使用下列格式之一：  
  
    -   若要發行至檔案共用或磁碟路徑，請使用 UNC 路徑中輸入的路徑 (*\\\Server\ApplicationName*) 或檔案路徑 (*C:\Deploy\ApplicationName*)。  
  
    -   若要發行至 FTP 伺服器，請輸入使用之格式的路徑*ftp://ftp.microsoft.com/\<應用程式名稱 >*。  
  
     請注意，文字必須存在於**發行位置**方塊中才能讓瀏覽 (**...**) 按鈕運作。  
  
## <a name="see-also"></a>另請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)