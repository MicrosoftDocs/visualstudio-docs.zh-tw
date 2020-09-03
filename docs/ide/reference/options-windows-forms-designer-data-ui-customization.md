---
title: 選項、Windows Form 設計工具、自訂資料欄位 UI
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e48777a50ddf66a8e5493698fb401ff7201de03e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114685"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>選項對話方塊： Windows Form 設計工具 > 資料 UI 自訂

此對話方塊會定義有哪些控制項會出現在 [資料來源] 視窗中可供項目使用的控制項清單中。 若要開啟它，請選取 [**工具**  >  **選項**]，然後選取 [ **Windows Form 設計工具**  >  **資料 UI 自訂**]。

您可以先從 [資料來源] 視窗中的某個項目上選取某個控制項，然後再將它拖曳到 Windows Forms 應用程式中的表單上。 可用的控制項是由項目的資料類型所決定。 每個資料類型都有一份有效相關聯控制項的清單 (如此對話方塊中所定義)，包括預設控制項。 當您從 [資料來源] 視窗將某個項目拖曳至表單上，而未選取控制項時，系統會將所選項目之資料類型的預設控制項加入該表單。

您可以選取及清除每個資料類型之可用控制項的核取方塊，以自訂相關聯控制項的清單。 若要將控制項加入清單，請將可實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 或 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 資料繫結屬性的控制項加入 [工具箱]。 該控制項將會出現在該資料類型的控制項清單中。 如需詳細資訊，請參閱 [如何：將自訂控制項加入至 [資料來源] 視窗](../..//data-tools/add-custom-controls-to-the-data-sources-window.md)。

## <a name="data-type"></a>資料類型

顯示能與控制項建立關聯的類型清單。 資料表是以 `[List]` 資料類型表示。 資料行是以基礎資料存放區中資料行的實際資料類型表示。

## <a name="associated-controls"></a>相關聯的控制項

顯示與所選資料類型相關聯的控制項清單。 選取或清除控制項旁的核取方塊以建立關聯或解除關聯。 選取的控制項會出現在已繫結至相關聯資料類型之資料庫資料行的 [資料來源] 視窗中。

## <a name="set-default"></a>設為預設值

將選取的控制項類型指派為所選資料類型的預設值。 在 [資料來源] 視窗中，預設控制項會顯示為資料庫資料行之捷徑功能表中的第一個選取項目。 當您從 [資料來源] 視窗將某個項目拖曳至表單上，而未選取控制項時，系統會將所選項目之資料類型的預設控制項加入該表單。

只能將單一控制項類型指派為某個資料類型的預設值。

## <a name="clear-default"></a>清除預設值

移除將某個控制項作為所選資料類型之預設值的指派。 如果選取的資料類型沒有預設值，則會在該類型之資料庫資料行的捷徑功能表中顯示 `[None]` 作為第一個選取項目。
