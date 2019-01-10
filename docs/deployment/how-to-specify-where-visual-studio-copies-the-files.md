---
title: 指定要複製的檔案位置 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
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
ms.openlocfilehash: ab842ce4f66684bf167d3cf627ce8cde82c5ea7c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830371"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>HOW TO：指定 Visual Studio 複製檔案的位置
當您使用 ClickOnce 發行應用程式時，`Publish Location`屬性會指定放置應用程式檔案和資訊清單的位置。 這可以是檔案路徑或 FTP 伺服器的路徑。  
  
 您可以在 [專案設計工具] 的 [發佈] 頁面上，或使用 [發佈精靈] 來指定 `Publish Location` 屬性。 如需詳細資訊，請參閱[＜How to：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
> [!NOTE]
>  當您使用 ClickOnce 安裝多個版本的應用程式時，安裝會將舊版應用程式移至您指定之發行位置中名為 Archive 的資料夾。 以這種方式封存先前的版本可將安裝目錄與舊版的資料夾分開。  
  
### <a name="to-specify-a-publishing-location"></a>指定發行位置  
  
1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2. 按一下 [發佈] 索引標籤。  
  
3. 在 [發佈位置] 欄位中，使用下列其中一種格式輸入發佈位置：  
  
   - 若要發佈至檔案共用或磁碟路徑，請使用 UNC 路徑 (*\\\Server\ApplicationName*) 或檔案路徑 (*C:\Deploy\ApplicationName*) 來輸入路徑。  
  
   - 若要發佈至 FTP 伺服器，請使用 <em>ftp://ftp.microsoft.com/\<ApplicationName></em> 格式來輸入路徑。  
  
     請注意，文字必須出現在 [發佈位置] 方塊中才能讓 [瀏覽] (**...**) 按鈕運作。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用 [發佈精靈] 發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)