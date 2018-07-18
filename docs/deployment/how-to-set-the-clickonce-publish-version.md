---
title: 如何： 設定 ClickOnce 發行版本 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96bb991efed7d5a353fc7b73bcb647190438ff84
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558330"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>如何：設定 ClickOnce 發行版本
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version`屬性會決定是否要發行應用程式將會被視為更新。 每個時間版本會遞增，應用程式將更新的形式發行。  
  
 `Publish Version`屬性可以設定上**發行**頁面**專案設計工具**。  
  
> [!NOTE]
>  將會自動遞增的專案選項`Publish Version`屬性每次發行應用程式，則預設會啟用此選項。 如需詳細資訊，請參閱[如何： 自動累加 ClickOnce 發行版本](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)。  
  
### <a name="to-change-the-publish-version"></a>若要變更的發行版本  
  
1.  選取方案總管 中的專案，然後按一下 [專案]  功能表中的 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  在**發行版本**欄位中，遞增**主要**，**次要**，**建置**，或**修訂**版本數字。  
  
    > [!NOTE]
    >  您應該永遠不會遞減的版本號碼;因此，這樣做可能會造成無法預期的更新行為。  
  
## <a name="see-also"></a>另請參閱  
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [如何：自動累加 ClickOnce 的發行版本](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)