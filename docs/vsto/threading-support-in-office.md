---
title: Office 中的執行緒支援
description: Microsoft Office 物件模型中支援執行緒。 Office 物件模型不具備執行緒安全，但可以在 Office 方案中使用多個執行緒。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5d44c86e17b5df79c44f85cd555b3036e925ae61
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524194"
---
# <a name="threading-support-in-office"></a>Office 中的執行緒支援
  本文提供 Microsoft Office 物件模型中如何支援執行緒的相關資訊。 Office 物件模型並非安全線程，但可以在 Office 方案中使用多個執行緒。 Office 應用程式是 COM) 伺服器 (元件物件模型。 COM 可讓用戶端呼叫任意執行緒上的 COM 伺服器。 若為不安全線程的 COM 伺服器，COM 會提供一種機制來序列化並行呼叫，如此一來，伺服器上一次只會執行一個邏輯執行緒。 這項機制稱為單一執行緒的單元 (STA) 模型。 由於呼叫是序列化的，因此呼叫端可能會在伺服器忙碌或處理背景執行緒上的其他呼叫時封鎖一段時間。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>使用多個執行緒時所需的知識
 若要使用多個執行緒，您必須至少具備多執行緒的下列層面的基本知識：

- Windows Api

- COM 多執行緒概念

- 並行

- 同步處理

- 封送處理

  如需多執行緒的一般資訊，請參閱 [Managed 執行緒](/dotnet/standard/threading/)。

  Office 會在主要 STA 中執行。 瞭解這項功能的含意，可以瞭解如何搭配使用多個執行緒與 Office。

## <a name="basic-multithreading-scenario"></a>基本多執行緒案例
 Office 方案中的程式碼一律會在主要 UI 執行緒上執行。 您可能想要在背景執行緒上執行個別的工作，以使應用程式效能變得更順暢。 其目標是要一次完成兩項工作，而不是一項工作，而不是另一項工作，這應該會導致執行更順暢， (使用多個執行緒) 的主要原因。 例如，您可能會在主要 Excel UI 執行緒上使用您的事件程式碼，而在背景執行緒上，您可能會執行工作以從伺服器收集資料，並使用伺服器中的資料來更新 Excel UI 中的資料格。

## <a name="background-threads-that-call-into-the-office-object-model"></a>呼叫 Office 物件模型的背景執行緒
 當背景執行緒呼叫 Office 應用程式時，會自動在 STA 界限之間封送處理呼叫。 但是，不保證 Office 應用程式在背景執行緒建立時可以處理呼叫。 有數種可能性：

1. Office 應用程式必須提取訊息，呼叫才有機會進入。 如果它正在執行繁重的處理，而未產生，則可能需要一些時間。

2. 如果單元中已有另一個邏輯執行緒，則新執行緒無法進入。 當邏輯執行緒進入 Office 應用程式，然後重新進入呼叫端的單元時，通常就會發生這種情況。 應用程式會被封鎖，等候該呼叫傳回。

3. Excel 可能處於無法立即處理撥入電話的狀態。 例如，Office 應用程式可能會顯示模式對話方塊。

   在可能性2和3中，COM 提供 [imessagefilter.prefiltermessage](/windows/desktop/api/objidl/nn-objidl-imessagefilter) 介面。 如果伺服器執行此方法，則所有呼叫都會透過 [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) 方法輸入。 在可能性2中，會自動拒絕呼叫。 在可能性3的情況下，伺服器可以拒絕呼叫，視情況而定。 如果拒絕呼叫，呼叫端必須決定要採取的動作。 一般情況下，呼叫端會執行 [imessagefilter.prefiltermessage](/windows/desktop/api/objidl/nn-objidl-imessagefilter)，在此情況下，會收到 [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) 方法拒絕的通知。

   但是，如果是使用 Visual Studio 中的 Office 開發工具所建立的方案，COM interop 會將所有拒絕的呼叫轉換 <xref:System.Runtime.InteropServices.COMException> ( 為「訊息篩選器指出應用程式忙碌中」 ) 。 當您在背景執行緒上進行物件模型呼叫時，您必須準備好處理這個例外狀況。 通常，這牽涉到重試一段特定的時間，然後顯示對話方塊。 不過，您也可以將背景執行緒建立為 STA，然後為該執行緒註冊訊息篩選器，以處理此情況。

## <a name="start-the-thread-correctly"></a>正確啟動執行緒
 當您建立新的 STA 執行緒時，請在啟動執行緒之前將單元狀態設定為 STA。 下列程式碼範例會示範如何執行這項操作。

 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]

 如需詳細資訊，請參閱 [Managed 執行緒最佳做法](/dotnet/standard/threading/managed-threading-best-practices)。

## <a name="modeless-forms"></a>非模式表單
 非強制回應表單可讓您在表單顯示時與應用程式進行某種類型的互動。 使用者會與表單互動，而表單會與應用程式互動，而不會關閉。 Office 物件模型支援 managed 非模式表單;但是，不應該在背景執行緒上使用它們。

## <a name="see-also"></a>另請參閱
- [執行緒 (c # ) ](/dotnet/csharp/programming-guide/concepts/threading/index)
- [執行緒處理 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [使用執行緒和執行緒](/dotnet/standard/threading/using-threads-and-threading)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
