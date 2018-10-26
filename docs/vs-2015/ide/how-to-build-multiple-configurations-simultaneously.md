---
title: 如何：同時建置多個組態 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa16c4c02f92f71d3288896d56b94a6d570c7dd4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930410"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>如何：同時建置多個組態
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 [批次建置] 對話方塊，同時建置具有多個甚至所有組建組態的多數類型專案。 不過，您無法同時在多個組建組態中組建下列類型的專案：  
  
1. [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 應用程式是使用 JavaScript 針對 Windows 建置。  
  
2. 所有 Visual Basic 專案。  
  
   如需組建組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。  
  
### <a name="to-build-a-project-in-multiple-build-configurations"></a>在多個組建組態中建置專案  
  
1.  在功能表列上，依序選擇 [建置] 和 [批次建置]。  
  
2.  在 [建置] 資料行中，選取您要用來建置專案之組態的核取方塊。  
  
    > [!TIP]
    >  若要編輯或建立方案的組建組態，請選擇功能表列上的 [建置]、[組態管理員] 以開啟 [組態管理員] 對話方塊。 在您編輯方案的組建組態之後，請在 [批次建置] 對話方塊中選擇 [重建] 按鈕，來更新方案中專案的所有組建組態。  
  
3.  選擇 [建置] 或 [重建] 按鈕，以使用您指定的組態來建置專案。  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)   
 [了解組建組態](../ide/understanding-build-configurations.md)   
 [同時建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)



