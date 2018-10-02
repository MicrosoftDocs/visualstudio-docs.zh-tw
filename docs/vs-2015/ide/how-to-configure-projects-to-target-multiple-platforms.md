---
title: 如何：將專案設定成以多重平台為目標 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 07c949e392ee2203804a8675a7659e71ced5c0fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498689"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>如何：將專案設定成以多重平台為目標
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[How to: Configure Projects to Target 多個平台](https://docs.microsoft.com/visualstudio/ide/how-to-configure-projects-to-target-multiple-platforms)。  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供方式，讓方案一次以數個不同 CPU 架構或平台為目標。 要設定這些項目的屬性是透過 [組態管理員] 對話方塊所存取。  
  
## <a name="targeting-a-platform"></a>以一個平台為目標  
 [組態管理員] 對話方塊可讓您建立與設定方案層級和專案層級的組態及平台。 每個方案層級組態和目標的組合都可以有唯一一組與建立關聯的屬性，例如，可讓您輕鬆地切換目標設為 [!INCLUDE[vcprx64](../includes/vcprx64-md.md)] 平台的版本組態、目標設為 x86 平台的版本組態，以及目標設為 x86 平台的偵錯組態。  
  
#### <a name="to-set-your-configuration-to-target-a-different-platform"></a>設定組態以將不同的平台設為目標  
  
1.  在 [建置] 功能表上，按一下 [組態管理員]。  
  
2.  在 [使用中的方案平台] 方塊中，選取您想要設為方案目標的平台，或選取 [\<新增>] 建立新的平台。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 將編譯您的應用程式，以將 [組態管理員] 對話方塊中設為使用中平台的平台設為目標。  
  
## <a name="removing-a-platform"></a>移除平台  
 如果您發現平台並不需要，則可以使用 [組態管理員] 對話方塊予以移除。 這會移除您針對該組態和目標組合所設定的所有方案和專案設定。  
  
#### <a name="to-remove-a-platform"></a>移除平台  
  
1.  在 [建置] 功能表上，按一下 [組態管理員]。  
  
2.  在 [使用中的方案平台] 方塊中，選取 [\<編輯>]。 [編輯方案平台] 對話方塊隨即開啟。  
  
3.  按一下您想要移除的平台，然後按一下 [移除]。  
  
## <a name="targeting-multiple-platforms-with-one-solution"></a>使用一個方案將多重平台設為目標  
 因為您可以根據組態與平台設定組合來變更設定，所以可以設定將多重平台設為目標的方案。  
  
#### <a name="to-target-multiple-platforms"></a>以多重平台為目標  
  
1.  使用 [組態管理員] 為方案至少新增兩個目標平台。  
  
2.  從 [使用中的方案平台] 清單中，選取您想要設為目標的平台。  
  
3.  建置方案。  
  
#### <a name="to-build-multiple-solution-configurations-at-once"></a>一次建置多個方案組態  
  
1.  使用 [組態管理員] 為方案至少新增兩個目標平台。  
  
2.  使用 [批次建置] 視窗，一次建置數個方案組態。  
  
 例如，可能會將方案層級平台設為 [!INCLUDE[vcprx64](../includes/vcprx64-md.md)]，而且以相同平台為目標的這個方案內沒有專案。 您的方案也可能有多個檔案，而且每個檔案都以不同的平台為目標。 建議，如果您有上述其中一種情況，則建立具有描述性名稱的新組態，以避免產生混淆。  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)   
 [了解組建組態](../ide/understanding-build-configurations.md)   
 [在 Visual Studio 中建置和清除專案與方案](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)



