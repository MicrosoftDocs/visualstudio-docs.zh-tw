---
title: Office 中的執行緒支援
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3218a12add86739c76cd50f82fdda5d845e2b069
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978763"
---
# <a name="threading-support-in-office"></a>Office 中的執行緒支援
  本文提供 Microsoft Office 物件模型中的執行緒支援方式的相關資訊。 Office 物件模型不是安全執行緒，但是仍可以使用 Office 方案中的多個執行緒。 Office 應用程式都是元件物件模型 (COM) 伺服器。 COM 可讓用戶端在任意的執行緒上呼叫 COM 伺服器。 不是安全執行緒的 COM 伺服器，COM 會提供一個機制來序列化，以便在任何時間只能有一個邏輯執行緒會執行伺服器上的並行呼叫。 這項機制稱為單一執行緒 apartment (STA) 模型。 因為呼叫已序列化，則呼叫端可能會封鎖，有一段時間伺服器忙碌中或正在處理其他背景執行緒上的呼叫時。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>使用多個執行緒時所需的知識
 若要使用多個執行緒，您必須至少基本知識的下列層面的多執行緒：

- Windows Api

- COM 多執行緒的概念

- 並行

- 同步處理

- 封送處理

  如需一般資訊相關的多執行緒處理，請參閱[受控執行緒](/dotnet/standard/threading/)。

  Office 執行中主要的 sta。 了解的含意，就可以了解如何使用 Office 中的多個執行緒。

## <a name="basic-multithreading-scenario"></a>基本的多執行緒案例
 在 Office 方案中的程式碼一定會在主要 UI 執行緒上執行。 您可以在背景執行緒上執行個別的工作平滑應用程式的效能。 目標是要完成兩項工作看似一次而不是一項工作後面接著另一個，這應該會導致更順暢的執行 （使用多個執行緒的主要原因）。 例如，您可能對主要的 Excel UI 執行緒中，您的事件程式碼，而，您可能會在背景執行緒上執行的工作，從伺服器收集資料，並使用來自伺服器的資料更新 Excel 的 UI 中的資料格。

## <a name="background-threads-that-call-into-the-office-object-model"></a>背景執行緒呼叫 Office 物件模型
 當背景執行緒進行 Office 應用程式的呼叫時，呼叫會自動封送處理跨 STA 界限。 不過，還有不保證在 Office 應用程式可以處理在背景執行緒進行的呼叫。 有數種可能性：

1. Office 應用程式必須提取呼叫有機會輸入的訊息。 如果它進行大量處理，但不產生這可能需要時間。

2. 如果另一個邏輯執行緒已在 apartment 中，無法輸入新的執行緒。 此外，這通常會發生於在邏輯執行緒進入 Office 應用程式，並使重新進入的呼叫傳回給呼叫端的 apartment。 應用程式會封鎖等候呼叫傳回。

3. Excel 可能處於的狀態，使它無法立即處理連入呼叫。 例如，Office 應用程式可能正在顯示強制回應對話方塊。

   2 和 3 的可能性，COM 會提供[IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter)介面。 透過伺服器實作它，如果輸入的所有呼叫[HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall)方法。 若為可能性 2，呼叫都會自動遭拒。 可能性 3，伺服器可以拒絕的呼叫中，視情況而定。 如果呼叫就會拒絕呼叫端必須決定該怎麼辦。 一般來說，呼叫者會實作[IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter)，在此情況下它會收到依拒絕[RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall)方法。

   不過，在 Visual Studio 中使用的 Office 開發工具所建立的方案，在 COM interop 將所有已拒絕的呼叫<xref:System.Runtime.InteropServices.COMException>（"訊息篩選器表示應用程式是忙碌中 」）。 每當您進行呼叫的物件模型時在背景執行緒，您必須準備好處理這個例外狀況。 一般而言，在包含重試一次針對一段時間，並顯示一個對話方塊。 不過，您也可以建立背景執行緒為 STA，然後註冊該執行緒來處理這種情況的訊息篩選器。

## <a name="start-the-thread-correctly"></a>正常啟動執行緒
 當您建立新的 STA 執行緒時，設定 apartment 狀態設為 STA 啟動執行緒之前。 下列程式碼範例會示範如何執行這項操作。

 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]

 如需詳細資訊，請參閱 < [Managed 執行緒最佳做法](/dotnet/standard/threading/managed-threading-best-practices)。

## <a name="modeless-forms"></a>非強制回應表單
 非強制回應表單在表單顯示時，可讓某種類型的應用程式的互動。 使用者所互動的表單和表單互動不需關閉應用程式。 Office 物件模型支援受管理的非強制回應表單。不過，它們不應在背景執行緒上。

## <a name="see-also"></a>另請參閱
- [執行緒 (C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [執行緒 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [使用執行緒和執行緒處理](/dotnet/standard/threading/using-threads-and-threading)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
