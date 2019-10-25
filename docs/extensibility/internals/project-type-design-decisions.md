---
title: 專案類型設計決策 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d6d1df2a3b2188360b0ee60480b4d6580ed8faf
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725384"
---
# <a name="project-type-design-decisions"></a>專案類型的設計決策
建立新的專案類型之前，您必須針對專案類型做出幾個設計決策。 您必須決定專案將包含哪些類型的專案、專案檔的保存方式，以及您要使用的承諾模型。

## <a name="project-items"></a>專案專案
 您的專案會使用檔案或抽象物件嗎？ 如果您使用檔案，它們會是參考型或目錄型檔案嗎？ 檔案或抽象物件將會在本機或遠端？

 專案中的專案可以是檔案，也可以是更抽象的物件，例如資料庫存放庫中的物件，或網際網路上的資料連線。 如果專案是檔案，專案可以是參考型或目錄型專案。

 在以參考為基礎的專案中，專案可以出現在多個專案中。 不過，專案所代表的實際檔案僅位於一個目錄中。 在以目錄為基礎的專案中，所有專案專案都存在於目錄結構中。

 本機專案會儲存在應用程式安裝所在的同一部電腦上。 遠端專案可以儲存在區域網路中的個別伺服器上，或存放在網際網路上的其他位置。

## <a name="project-file-persistence"></a>專案檔案持續性
 資料會儲存在一般的一般檔案系統或結構化儲存體中嗎？ 檔案會使用標準編輯器或專案特定編輯器來開啟嗎？

 為了保存其資料，大部分的應用程式會將其資料儲存在檔案中，然後在使用者必須檢查或變更資訊時將其讀回。

 結構化儲存體（也稱為複合檔案）通常會在數個元件物件模型（COM）物件需要將保存的資料儲存在單一檔案中時使用。 使用結構化存放裝置，有數個不同的軟體元件可以共用單一磁片檔案。

 您有數個選項可以考慮專案中專案的持續性。 您可以執行下列任何一個選項：

- 當每個檔案變更時，個別儲存每個檔案。

- 在單一**儲存**作業中捕捉許多交易。

- 將檔案儲存在本機，然後發行至伺服器，或使用另一種方法來儲存專案專案（當專案代表與遠端物件的資料連線時）。

  如需持續性的詳細資訊，請參閱[專案持續](../../extensibility/internals/project-persistence.md)性和[開啟和儲存專案專案](../../extensibility/internals/opening-and-saving-project-items.md)。

## <a name="project-commitment-model"></a>專案承諾模型
 保存的資料物件會以 direct 模式或交易模式開啟嗎？

 以 direct 模式開啟資料物件時，對資料所做的變更會立即納入，或在使用者手動儲存檔案時。

 當使用交易模式來開啟資料物件時，變更會儲存到記憶體中的暫存位置，而且在使用者手動選擇儲存檔案之前，不會進行認可。 此時，所有變更都必須一起發生，否則將不會進行任何變更。

## <a name="see-also"></a>請參閱
- [檢查清單︰建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)
- [專案持續性](../../extensibility/internals/project-persistence.md)
- [專案模型的元素](../../extensibility/internals/elements-of-a-project-model.md)
- [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)
- [建立專案類型](../../extensibility/internals/creating-project-types.md)