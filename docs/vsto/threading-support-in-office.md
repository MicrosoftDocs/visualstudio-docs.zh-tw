---
title: Office 中的執行緒支援
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 966f012b2ff4860205186410951b759c2e214668
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693080"
---
# <a name="threading-support-in-office"></a>Office 中的執行緒支援
  本文提供 Microsoft Office 物件模型中的執行緒支援方式的相關資訊。 Office 物件模型不具備執行緒安全，但您可使用 Office 方案中的多個執行緒。 Office 應用程式的元件物件模型 (COM) 伺服器。 COM 可讓用戶端在任意的執行緒上呼叫 COM 伺服器。 不是安全執行緒的 COM 伺服器，COM 會提供序列化並行呼叫，以便在任何時間只能有一個邏輯執行緒會執行伺服器上的機制。 這項機制稱為單一執行緒 apartment (STA) 模型。 呼叫已序列化，因為呼叫端可能會封鎖一段時間，伺服器忙碌中或正在處理其他背景執行緒上的呼叫時。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>使用多個執行緒時所需的知識  
 若要使用多個執行緒，您必須至少基本知識的下列層面多執行緒：  
  
-   Windows 應用程式開發介面  
  
-   COM 多執行緒的概念  
  
-   並行  
  
-   同步處理  
  
-   封送處理  
  
 如需一般資訊相關的多執行緒處理，請參閱[Managed 執行緒處理](/dotnet/standard/threading/)。  
  
 Office 會執行在主要 sta。 了解的影響將讓您能夠了解如何使用 Office 中的多個執行緒。  
  
## <a name="basic-multithreading-scenario"></a>基本的多執行緒案例  
 在 Office 方案中的程式碼一定會主要 UI 執行緒上執行。 您可以藉由背景執行緒上執行的個別工作平滑應用程式效能。 目標是要完成兩項工作表面上一次而不是一項工作後面接著另一個，這應該會導致更順暢的執行 （使用多個執行緒的主要原因）。 例如，主要的 Excel UI 執行緒，可能您事件的程式碼，您可能會在背景執行緒上執行的工作，從伺服器收集資料，並使用來自伺服器的資料更新 Excel UI 中的資料格。  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>背景執行緒呼叫 Office 物件模型  
 當背景執行緒會在 Office 應用程式呼叫時，呼叫會自動封送處理跨 STA 界限。 不過，沒有保證在 Office 應用程式可以處理在背景執行緒進行的呼叫。 有數種可能性：  
  
1.  Office 應用程式必須呼叫有機會輸入訊息幫浦 」。 如果正在進行重大的不含退讓處理可能需要時間。  
  
2.  如果另一個邏輯執行緒已在 apartment 中，無法輸入新的執行緒。 這通常會發生邏輯執行緒進入 Office 應用程式，並可重新進入的呼叫傳回給呼叫者的 apartment。 應用程式會封鎖該呼叫以傳回正在等候。  
  
3.  Excel 可能處於的狀態，使它無法立即處理的傳入呼叫。 例如，Office 應用程式可能正在顯示強制回應對話方塊。  
  
 COM 會提供 2 和 3 的可能性， [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248)介面。 透過伺服器實作它，如果輸入的所有呼叫[HandleIncomingCall](http://msdn.microsoft.com/en-us/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be)方法。 可能性 2，呼叫都會自動遭拒。 可能性 3，伺服器可以拒絕的呼叫，視情況而定。 如果已拒絕呼叫，呼叫端必須決定要執行的工作。 一般來說，呼叫端實作[IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248)，拒絕動作的在此情況下會收到通知[RetryRejectedCall](http://msdn.microsoft.com/en-us/3f800819-2a21-4e46-ad15-f9594fac1a3d)方法。  
  
 不過，如果是使用 Visual Studio 中的 Office 開發工具所建立的方案，COM interop 轉換所有已拒絕的呼叫<xref:System.Runtime.InteropServices.COMException>（"訊息篩選條件以表示應用程式是忙碌中 」）。 每當您進行呼叫的物件模型在背景執行緒，您必須準備好處理這個例外狀況。 一般而言，牽涉到重試的時間量，並顯示對話方塊。 不過，也會建立為 STA 背景執行緒，然後再註冊該執行緒來處理這種情況的訊息篩選條件。  
  
## <a name="start-the-thread-correctly"></a>正確地啟動執行緒  
 當您建立新的 STA 執行緒時，apartment 狀態設定為 STA 啟動執行緒之前。 下列程式碼範例會示範如何執行這項操作。  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 如需詳細資訊，請參閱[Managed 執行緒處理最佳作法](/dotnet/standard/threading/managed-threading-best-practices)。  
  
## <a name="modeless-forms"></a>非強制回應表單  
 非強制回應表單可讓某種類型的應用程式互動時顯示表單。 使用者互動的表單，並與未關閉應用程式互動的表單。 Office 物件模型支援受管理的非強制回應表單。不過，它們不應在背景執行緒上。  
  
## <a name="see-also"></a>另請參閱  
 [Managed 執行緒處理](/dotnet/standard/threading/)  
 [執行緒處理 (C#)](/dotnet/csharp/programming-guide/concepts/threading/index) [執行緒 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [使用執行緒和執行緒處理](/dotnet/standard/threading/using-threads-and-threading)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
  
  