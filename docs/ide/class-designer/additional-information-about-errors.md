---
title: 類別設計工具錯誤
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- error messages, class diagrams
- Class Designer [Visual Studio], errors
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cfafcedae225522ec71e0bc35854d827047af2fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53901684"
---
# <a name="class-designer-errors"></a>類別設計工具錯誤

**類別設計工具**不會追蹤原始程式檔的位置，因此，修改您的專案結構或移動專案中的原始程式檔，可能會導致**類別設計工具**無法繼續追蹤類型，舉例來說，修改 typedef、基底類別和關聯類型的來源類型都很常見。 您可能會收到錯誤，例如：**類別設計工具無法顯示這個類型**。 若要解決錯誤，請將修改或重新放置的原始程式碼再次拖曳到類別圖表中，使其顯示。

## <a name="resources"></a>資源

您可以在下列資源中找到其他錯誤和警告的協助：

- [使用 Visual C++ 程式碼](working-with-visual-cpp-code.md)包括有關在類別圖表中顯示 C++ 的疑難排解資訊。
- [Visual Studio 類別設計工具論壇](http://go.microsoft.com/fwlink/?LinkId=160754)提供**類別設計工具**相關問題的論壇。

## <a name="see-also"></a>另請參閱

- [設計和檢視類別及類型](designing-and-viewing-classes-and-types.md)
