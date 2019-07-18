---
title: 作法：自動累加 ClickOnce 的發行版本 |Microsoft Docs
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683915"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>作法：自動累加 ClickOnce 的發行版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

發佈時[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式中，變更`Publish Version`屬性可讓應用程式以更新形式發行。 根據預設，Visual Studio 會自動遞增`Revision`數目`Publish Version`每次發行應用程式。  
  
 您可以在停用此行為**發佈**頁**專案設計工具**。  
  
> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>若要停用 自動遞增發行版本  
  
1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2. 按一下 [發佈] 索引標籤。  
  
3. 在 **發行版本**區段中，清除**隨著每次發行自動遞增修訂**核取方塊。  
  
## <a name="see-also"></a>另請參閱  
 [如何：設定 ClickOnce 發行版本](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用 [發佈精靈] 發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
