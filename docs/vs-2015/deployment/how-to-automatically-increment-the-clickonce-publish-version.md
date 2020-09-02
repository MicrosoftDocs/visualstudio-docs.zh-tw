---
title: 如何：自動遞增 ClickOnce 發行版本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 50faf70e8eda6ef7ab01201102540729497eb87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683915"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>如何：自動累加 ClickOnce 的發行版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

發行 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式時，變更 `Publish Version` 屬性會導致應用程式發佈為更新。 依預設，Visual Studio 會在 `Revision` `Publish Version` 每次發行應用程式時自動遞增的數目。  
  
 您可以在 [**專案設計**工具] 的 [**發行**] 頁面上停用此行為。  
  
> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具]**** 功能表上選擇 [匯入和匯出設定]****。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>若要停用自動遞增發行版本  
  
1. 在方案總管 **** 中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。  
  
2. 按一下 [Publish (發行)] **** 索引標籤。  
  
3. 在 [ **發行版本** ] 區段中，清除 [ **自動遞增修訂與每個版本** ] 核取方塊。  
  
## <a name="see-also"></a>另請參閱  
 [如何：設定 ClickOnce 發行版本](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發佈嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
