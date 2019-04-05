---
title: 使用舊版狀態機器工作流程設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e96d1db524d5a80a9f298fa84ca1ccf27e28fbf4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930027"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>使用舊版狀態機器工作流程設計工具
建立在新的狀態機器工作流程專案時[!INCLUDE[vs2010](../includes/vs2010-md.md)]為目標的其中一個[!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]或[!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]，您可以選擇使用任何一種**狀態機器工作流程主控台應用程式**或**狀態機器工作流程程式庫**舊版專案範本。 如果您選擇其中一個狀態機器專案範本，則狀態機器設計工具會以舊版工作流程設計工具使用者介面的方式呈現。 如需舊版狀態機器專案範本的詳細資訊，請參閱[How to:建立狀態機器工作流程主控台應用程式 （舊版）](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)和[How to:建立狀態機器工作流程程式庫 （舊版）](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)。  
  
 狀態機器工作流程包含了一組狀態。 其中有一個狀態表示初始狀態。 每個狀態可以接收特定的一組事件。 根據事件，會完成另一個狀態的轉換。 狀態機器工作流程會有最終狀態。 當轉換為最終狀態時，工作流程便完成。  
  
## <a name="state-machine-designer-views"></a>狀態機器設計工具檢視  
 狀態機器設計工具是不限格式的設計工具，這表示活動可自由地在設計介面上移動。 狀態機器設計工具有兩個檢視：*狀態*檢視和*事件導向*檢視。  
  
 狀態檢視會顯示狀態活動和可包含在狀態活動中的事件驅動活動。 在這個檢視中，從某一個狀態的事件驅動活動延伸到另一個狀態的線條，表示狀態之間的轉換。 您也可以自行繪製線條來建立轉換。 若要繪製轉換，請選取事件驅動活動，再選取該活動上的其中一個控點，然後拖曳。 這個動作會繪製出一條直線。 接著將這條線連接到目標狀態，表示狀態間的轉換。  
  
 若要存取事件驅動檢視，請按兩下事件驅動活動。 顯示的設計工具和循序工作流程設計工具非常像。 設計工具的頂端是巡覽列，後者會顯示所有活動的階層直到事件驅動活動顯示為止。 您可以按一下所顯示階層中的任何項目，巡覽回狀態檢視。 如果您已在狀態檢視中繪製出狀態間的轉換，而且顯示的是該活動的事件驅動檢視，則會為您將設定狀態活動新增至事件驅動活動。 如果您變更該設定狀態活動的屬性，會反映到狀態檢視中。  
  
## <a name="state-machine-workflow-activities"></a>狀態機器工作流程活動  
 下表說明狀態機器工作流程設計工具中使用的重要活動：  
  
|工具箱名稱|活動|描述|  
|------------------|--------------|-----------------|  
|**狀態**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|代表狀態機器; 中的狀態可能包含其他**StateActivity**活動。 如需詳細資訊，請參閱 <<c0> [ 使用 StateActivity 活動](http://go.microsoft.com/fwlink?LinkID=65083)。|  
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|指定轉換至新狀態。 如需詳細資訊，請參閱 <<c0> [ 使用 SetStateActivity 活動](http://go.microsoft.com/fwlink?LinkID=65082)。|  
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|輸入狀態時執行，可能包含其他活動。 如需詳細資訊，請參閱 <<c0> [ 使用 StateInitialization 活動](http://go.microsoft.com/fwlink?LinkID=65006)。|  
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|執行包含的活動時離開[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)活動。 如需詳細資訊，請參閱 <<c0> [ 使用 StateFinalizationActivity 活動](http://go.microsoft.com/fwlink?LinkID=65008)。|  
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|用於信賴外部事件以啟動執行的狀態。 **EventDrivenActivity**活動必須有活動實作[IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032)介面做為第一個子活動。 如需詳細資訊，請參閱 <<c0> [ 使用 EventDrivenActivity 活動](http://go.microsoft.com/fwlink?LinkID=65068)。|  
  
 狀態機器工作流程中的主要元件是[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)活動。 在狀態機器工作流程中的各種點捕捉到事件時，會進入不同的狀態來處理與事件相關聯的工作。 在工作流程的存留期中，工作流程會離開並進入數個不同的狀態。 使用這些狀態連接到彼此[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)活動。  
  
 當您將新**StateActivity**拖曳至工作流程設計介面中，您可以新增[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)， [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)， [StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)，或其他**StateActivity**做為子活動的活動。  
  
> [!CAUTION]
>  當您使用狀態機器工作流程設計工具來建立工作流程時，您必須監視工作流程，您要設計與結構**文件大綱**檢視 視窗中。 結構中的狀態機器工作流程的檢視**文件大綱**視窗鏡像的工作流程標記檔案中的活動邏輯版面配置 檢視。 當工作流程活動出現在設計介面時，其實體配置可能不會鏡像工作流程標記檔案中活動的邏輯配置。  
>   
>  若要開啟 [**文件大綱**] 視窗，請在**檢視**功能表上，指向**其他 Windows**，然後選取**文件大綱**。  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立狀態機器工作流程主控台應用程式 （舊版）](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)   
 [如何：建立狀態機器工作流程程式庫 （舊版）](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)   
 [狀態機器工作流程](http://go.microsoft.com/fwlink?LinkID=65016)   
 [使用 StateActivity 活動](http://go.microsoft.com/fwlink?LinkID=65083)   
 [使用 StateInitializationActivity 活動](http://go.microsoft.com/fwlink?LinkID=65006)   
 [使用 StateFinalizationActivity 活動](http://go.microsoft.com/fwlink?LinkID=65008)   
 [使用 SetStateActivity 活動](http://go.microsoft.com/fwlink?LinkID=65082)   
 [使用 EventDrivenActivity 活動](http://go.microsoft.com/fwlink?LinkID=65068)