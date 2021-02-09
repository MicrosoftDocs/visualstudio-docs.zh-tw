---
title: 專案類型設計決策 |Microsoft Docs
description: 藉由建立新的專案類型，瞭解您在擴充 Visual Studio 之前所要進行的專案、專案檔持續性和承諾用量技師修理設計決策。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d1b051abfede6ec90350878f669ed32e7e26b299
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896753"
---
# <a name="project-type-design-decisions"></a>專案類型的設計決策
建立新的專案類型之前，您必須針對您的專案類型進行數個設計決策。 您必須決定專案將包含哪些類型的專案、專案檔的保存方式，以及您將使用的承諾用量模型。

## <a name="project-items"></a>專案項目
 您的專案會使用檔案或抽象物件嗎？ 如果您使用檔案，它們會是以參考為基礎或以目錄為基礎的檔案嗎？ 檔案或抽象物件將會位於本機或遠端？

 專案中的專案可以是檔案，也可以是更抽象的物件，例如資料庫存放庫中的物件或網際網路上的資料連線。 如果專案是檔案，則專案可以是以參考為基礎或以目錄為基礎的專案。

 在以參考為基礎的專案中，專案可以出現在多個專案中。 不過，專案所代表的實際檔案僅位於單一目錄中。 在以目錄為基礎的專案中，所有專案專案都存在於目錄結構中。

 本機專案會儲存在安裝應用程式的同一部電腦上。 遠端專案可以儲存在區域網路或網際網路上其他位置的不同伺服器上。

## <a name="project-file-persistence"></a>專案檔案持續性
 資料會儲存在一般的一般檔案系統或結構化儲存體中？ 檔案會使用標準編輯器或專案特定的編輯器來開啟嗎？

 為了保存其資料，大部分的應用程式都會將其資料儲存在檔案中，然後在使用者必須檢查或變更資訊時將其讀回。

 結構化儲存體（也稱為複合檔案）通常會在數個元件物件模型 (COM) 物件需要將其保存的資料儲存在單一檔案時使用。 使用結構化儲存體時，有數個不同的軟體元件可以共用單一磁片檔。

 您有數個選項可以考慮專案中專案的持續性。 您可以執行下列任何一個選項：

- 在檔案變更時個別儲存檔案。

- 在單一 **儲存** 作業中捕捉許多交易。

- 在本機儲存檔案，然後發行至伺服器，或使用另一種方法來儲存專案專案，而該專案代表與遠端物件的資料連線。

  如需持續性的詳細資訊，請參閱 [專案持續](../../extensibility/internals/project-persistence.md) 性和 [開啟和儲存專案專案](../../extensibility/internals/opening-and-saving-project-items.md)。

## <a name="project-commitment-model"></a>專案承諾用量模型
 保存的資料物件會以直接模式或交易模式開啟嗎？

 當資料物件以直接模式開啟時，對資料所做的變更會立即或在使用者手動儲存檔案時合併。

 使用交易模式開啟資料物件時，變更會儲存到記憶體中的暫存位置，而且在使用者手動選擇儲存檔案之前，不會認可這些變更。 屆時，所有變更都必須一起進行，否則也不會進行任何變更。

## <a name="see-also"></a>另請參閱
- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)
- [專案持續性](../../extensibility/internals/project-persistence.md)
- [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)
- [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)
- [建立專案類型](../../extensibility/internals/creating-project-types.md)
