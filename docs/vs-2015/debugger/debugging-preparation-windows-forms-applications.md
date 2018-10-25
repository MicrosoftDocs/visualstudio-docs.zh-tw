---
title: 偵錯準備： Windows Forms 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [J#], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5877bcf4501125968e2fb14f56c41c1ccbc9e561
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885131"
---
# <a name="debugging-preparation-windows-forms-applications"></a>偵錯準備：Windows Forms 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Form 專案範本會建立 Windows Forms 應用程式。 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中可以直接偵錯這種類型的應用程式。 如需詳細資訊，請參閱 <<c0> [ 建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
 當您以專案範本建立 Windows Form 專案時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會自動建立偵錯和發行組態所需要的設定。 若有需要，您可以變更這些設定。 可以變更這些設定，在**\<專案名稱 > 屬性頁** 對話方塊 (**我的專案**Visual Basic 中)。  
  
 如需詳細資訊，請參閱 <<c0> [ 建議的屬性設定](../debugger/managed-debugging-recommended-property-settings.md)。  
  
 下表顯示一個額外的建議屬性設定。  
  
### <a name="configuration-properties-in-debug-tab"></a>偵錯索引標籤的組態屬性  
  
|**屬性名稱**|**設定**|  
|-----------------------|-----------------|  
|**啟動動作**|-設定為**入門專案**大部分的情況。 設定為**啟動外部程式**如果您想要啟動可執行檔的另一個您啟動偵錯時 （通常適用於偵錯 Dll）。|  
  
 您可以從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 內部偵錯 Windows Forms 應用程式，或附加至正在執行的應用程式進行偵錯。 如需附加的詳細資訊，請參閱 <<c0> [ 附加至執行的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>若要偵錯 C#、F# 或 Visual Basic Windows Forms 應用程式  
  
1. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中開啟專案。  
  
2. 建立需要的中斷點。  
  
    因為 Windows Forms 應用程式是事件驅動的，您的中斷點會進入事件處理常式程式碼中，或事件處理常式程式碼所呼叫的方法中。 通常放置中斷點的事件包括：  
  
   1. 與控制項相關的事件，例如點選、輸入等等。  
  
   2. 與啟動和關閉應用程式有關的事件，例如載入、啟動等等。  
  
   3. 焦點和驗證事件。  
  
      如需詳細資訊，請參閱[在 Windows Forms 中建立事件處理常式](http://msdn.microsoft.com/library/6514e530-c6b8-489c-a8d2-eda7b7072701)。  
  
3. 在 **偵錯**功能表上，按一下**開始**。  
  
4. 使用所述的技巧進行偵錯[偵錯工具基本概念](../debugger/debugger-basics.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [C#、F# 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [如何： 設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)   
 [C# 偵錯設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [附加至執行中處理程序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](http://msdn.microsoft.com/library/627df1e9-b254-41af-bbac-9a4f02810c54)



