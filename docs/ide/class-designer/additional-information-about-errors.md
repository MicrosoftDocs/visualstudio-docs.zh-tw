---
title: 類別設計工具錯誤
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc8b2c013a3e685a6071f4a12d63e3ca475051a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596511"
---
# <a name="class-designer-errors"></a>類別設計工具錯誤

**類別設計工具**不會追蹤原始程式檔的位置，因此，修改您的專案結構或移動專案中的原始程式檔，可能會導致**類別設計工具**無法繼續追蹤類型，舉例來說，修改 typedef、基底類別和關聯類型的來源類型都很常見。 您可能會收到錯誤，例如：**類別設計工具無法顯示這個類型**。 若要解決錯誤，請將修改或重新放置的原始程式碼再次拖曳到類別圖表中，使其顯示。

## <a name="resources"></a>資源

您可以在下列資源中找到其他錯誤和警告的協助：

- [使用 Visual C++ 程式碼](working-with-visual-cpp-code.md)包括有關在類別圖表中顯示 C++ 的疑難排解資訊。
- [Visual Studio 類別設計工具論壇](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner)提供**類別設計工具**相關問題的論壇。

## <a name="see-also"></a>另請參閱

- [設計和查看類別和類型](designing-and-viewing-classes-and-types.md)
