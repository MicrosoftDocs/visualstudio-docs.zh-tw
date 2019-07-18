---
title: 專案類型的設計決策 |Microsoft Docs
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
ms.openlocfilehash: 697b09ff5725de954963f7583271ac9ebd6814a8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328114"
---
# <a name="project-type-design-decisions"></a>專案類型的設計決策
建立新的專案類型之前，您必須對您的專案類型數個設計決策。 您必須決定您將使用哪些類型的項目會包含您的專案、 如何將保存專案檔，以及哪一種承諾用量的模型。

## <a name="project-items"></a>專案項目
 將您的專案會使用檔案或抽象物件？ 如果您使用檔案時，他們會參考或目錄為基礎的檔案嗎？ 會為本機或遠端的檔案或抽象的物件，要嗎？

 在專案中的項目可以是檔案，或它們可以跨網際網路更抽象的物件，例如在資料庫中的存放庫或資料連線 中的物件。 如果項目是檔案、 專案可以參考為基礎或 directory 為基礎的專案。

 在參考為基礎的專案中，項目可以出現在多個專案。 不過，實際項目表示的檔案位於中只有一個目錄。 在目錄型專案中，所有專案項目會存都在於目錄結構中。

 本機項目會儲存應用程式安裝所在的同一部電腦上。 遠端的項目可以儲存在本機網路中，不同的伺服器上或在網際網路上其他位置。

## <a name="project-file-persistence"></a>專案檔案持續性
 將資料儲存在通用的一般檔案系統中，或結構化儲存體中？ 會使用標準的編輯器或專案特定編輯器開啟檔案嗎？

 若要保留其資料，大部分的應用程式會將其資料儲存在檔案中，，，然後將之讀取後使用者必須檢閱或變更的資訊。

 結構化儲存體，也稱為複合檔案，通常是在數個元件物件模型 (COM) 物件需要將其保存的資料儲存在單一檔案時使用。 使用結構化儲存體，數個不同的軟體元件可以共用單一磁碟的檔案。

 您有數個選項需要考慮您的專案中的項目之持續性。 您可以執行任何下列其中一個選項：

- 已變更時，分別儲存每個檔案。

- 擷取在單一的許多交易**儲存**作業。

- 儲存在本機將檔案然後發行到伺服器，或使用另一個方法，來儲存專案項目，當項目所表示的遠端物件的資料連接。

  如需持續性的詳細資訊，請參閱[專案持續性](../../extensibility/internals/project-persistence.md)並[開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)。

## <a name="project-commitment-model"></a>專案的承諾模型
 將保存的資料物件會開啟在直接模式 」 或 「 交易的模式？

 時資料物件會在直接模式中開啟，或當使用者以手動方式儲存檔案時，立即併入對資料所做的變更。

 當使用交易的模式時，會開啟資料物件時，變更會儲存到記憶體中的暫存位置，和未認可，直到使用者手動選擇要儲存檔案。 此時，所有的變更必須一起出現，或會進行任何變更。

## <a name="see-also"></a>另請參閱
- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)
- [專案持續性](../../extensibility/internals/project-persistence.md)
- [專案模型的元素](../../extensibility/internals/elements-of-a-project-model.md)
- [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)
- [建立專案類型](../../extensibility/internals/creating-project-types.md)