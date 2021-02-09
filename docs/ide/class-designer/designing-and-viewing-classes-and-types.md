---
title: 使用類別設計工具
description: 瞭解如何使用 Visual Studio 中的類別設計工具來設計、視覺化及重構程式碼中的類別和其他類型。
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
- vs.classdesigner.enum
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 236efe20ee652e2690cedf36843d539bf8a9cc46
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850291"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>使用類別設計工具設計及檢視類別和類型

使用 Visual Studio 中的 **類別設計工具** 來設計、視覺化及重構程式碼中的類別和其他類型。 您可以使用類別圖表來建立和編輯 C#、Visual Basic 或 C++ 專案中的類別。 也可以使用類別圖表來進一步了解您的專案結構，或重新組織您的程式碼。

## <a name="what-you-can-do-with-class-diagrams"></a>您可以使用類別圖表來執行的工作

- **設計**：藉由編輯類別圖表來編輯您的專案程式碼。 加入新元素，並刪除不需要的元素。 您的變更會反映在程式碼中。

- **視覺化**：在圖表上檢視專案中的類別，以了解專案的結構。 自訂您的圖表，讓您可以專注在您最關心的專案詳細資料。 儲存您的圖表，以供日後用於示範或說明文件。

- **重構**：覆寫方法、重新命名識別碼、重構參數，以及實作介面和抽象類別。

## <a name="view-types-and-relationships"></a>檢視類型與關聯性

類別圖表會顯示類型的詳細資料，例如其關係人成員，以及成員之間的關聯性。 這些實體在視覺化後，即為程式碼的動態檢視。 這表示您可以在設計工具上編輯類型，然後就能看到編輯的結果反映在實體的原始程式碼中。 同樣地，類別圖表會與您對程式碼檔案進行地變更保持同步。

> [!NOTE]
> 如果您的專案包含類別圖表，而且參考了其他專案中的類型，則除非您建置該類型的專案，否則類別圖表不會顯示參考的類型。 同樣地，除非您重建外部實體的專案，否則此圖表不會顯示該實體的程式碼變更。

## <a name="class-diagram-workflow"></a>類別圖表工作流程

類別圖表可協助您了解專案的類別結構。 這些專案可能是由其他開發人員建立的，或您只是想在自己建立的專案上使用重新整理工具。 您可以使用這些類別圖表來自訂專案資訊、與其他人共用，以及向其他人展示。

展示專案資訊的第一個步驟，就是建立可顯示您要展示之內容的類別圖表。 如需詳細資訊，請參閱[新增類別圖表](how-to-add-class-diagrams-to-projects.md)。 您可以為一個專案建立多個類別圖表，以用來顯示專案的不同檢視、所選擇的專案類型子集，或所選擇的類型成員子集。

除了定義每個類別圖表所顯示的內容，您也可以變更資訊的呈現方式;如需詳細資訊，請參閱 [如何：自訂類別圖表](how-to-customize-class-diagrams.md)。

微調過一或多個類別圖表之後，您可以將其複製到 Microsoft Office 文件並加以列印，或將其匯出成影像檔。 如需詳細資訊，請參閱 [如何：將類別圖表元素複製到 Microsoft Office 檔](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md)、 [如何：列印類別](how-to-print-class-diagrams.md) 圖表和 [如何：將類別圖表匯出為影像](how-to-export-class-diagrams-as-images.md)。

> [!NOTE]
> 類別設計工具不會追蹤原始程式檔的位置，因此，變更您的專案結構或移動專案中的原始程式檔，可能會導致類別設計工具遺失類型的追蹤，特別是 typedef、基底類別或關聯類型的來源類型。 您可能會收到錯誤，例如：**類別設計工具無法顯示這個類型**。 如果您收到錯誤訊息，請將已修改或重新配置的原始程式碼再次拖曳到類別圖表中，以重新顯示。

## <a name="see-also"></a>另請參閱

- [程式碼編輯器的功能](../writing-code-in-the-code-and-text-editor.md)
- [對應方案之間的相依性](../../modeling/map-dependencies-across-your-solutions.md)
