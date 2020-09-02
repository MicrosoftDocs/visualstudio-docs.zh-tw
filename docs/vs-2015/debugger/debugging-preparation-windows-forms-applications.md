---
title: 偵錯工具準備： Windows Forms 應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b11855fbd19dc464f92b4339684ef8346556c21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691154"
---
# <a name="debugging-preparation-windows-forms-applications"></a>偵錯準備：Windows Forms 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Form 專案範本會建立 Windows Forms 應用程式。 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中可以直接偵錯這種類型的應用程式。 如需詳細資訊，請參閱 [建立 Windows 應用程式專案](https://msdn.microsoft.com/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
 當您以專案範本建立 Windows Form 專案時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會自動建立偵錯和發行組態所需要的設定。 若有需要，您可以變更這些設定。 您可以在 [ ** \<project name> 屬性頁**] 對話方塊中變更這些設定， (**我的專案**在 Visual Basic) 中。  
  
 如需詳細資訊，請參閱 [建議的屬性設定](../debugger/managed-debugging-recommended-property-settings.md)。  
  
 下表顯示一個額外的建議屬性設定。  
  
### <a name="configuration-properties-in-debug-tab"></a>偵錯索引標籤的組態屬性  
  
|**屬性名稱**|**設定**|  
|-----------------------|-----------------|  
|**啟動執行**|-   通常會設定為 [起始專案]****。 如果您開始偵錯 (通常是偵錯 DLL) 時想要啟動另外一個可執行檔，請設定為 [啟動外部程式]****。|  
  
 您可以從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 內部偵錯 Windows Forms 應用程式，或附加至正在執行的應用程式進行偵錯。 如需附加的詳細資訊，請參閱 [附加至正在](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)執行的進程。  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>若要偵錯 C#、F# 或 Visual Basic Windows Form 應用程式  
  
1. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中開啟專案。  
  
2. 建立需要的中斷點。  
  
    因為 Windows Form 應用程式是事件驅動的，您的中斷點會進入事件處理常式程式碼中，或事件處理常式程式碼所呼叫的方法中。 通常放置中斷點的事件包括：  
  
   1. 與控制項相關的事件，例如點選、輸入等等。  
  
   2. 與啟動和關閉應用程式有關的事件，例如載入、啟動等等。  
  
   3. 焦點和驗證事件。  
  
      如需詳細資訊，請參閱[在 Windows Forms 中建立事件處理常式](https://msdn.microsoft.com/library/6514e530-c6b8-489c-a8d2-eda7b7072701)。  
  
3. 在 **[偵錯]** 功能表中，按一下 **[啟動]**。  
  
4. 使用調試 [程式基本概念](../debugger/debugger-basics.md)中所討論的技術進行 Debug。  
  
## <a name="see-also"></a>另請參閱  
 [Managed 程式碼的偵錯工具](../debugger/debugging-managed-code.md)   
 [C #、F # 和 Visual Basic 專案類型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [How to：設定 Debug 和 Release 設定](../debugger/how-to-set-debug-and-release-configurations.md)   
 [C # Debug 設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic Debug 設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [附加至正在執行的進程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](https://msdn.microsoft.com/library/627df1e9-b254-41af-bbac-9a4f02810c54)
