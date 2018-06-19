---
title: 專案類型的設計決策 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c28c6f29454feed94407d6e37c3432247b9a4a26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131486"
---
# <a name="project-type-design-decisions"></a>專案類型的設計決策
建立新的專案類型之前，您必須決定數個設計有關您的專案類型。 您必須決定您將使用哪些類型的專案將包含的項目、 如何將保存專案檔，以及哪一種承諾模型。  
  
## <a name="project-items"></a>專案項目  
 將您的專案會使用檔案或抽象物件？ 如果您使用檔案時，他們會參考或目錄為基礎的檔案嗎？ 會為本機或遠端的檔案或抽象物件進行作業嗎？  
  
 在專案中的項目可以是檔案，或在網際網路上可以更抽象物件，例如資料庫儲存機制或資料連接中的物件。 如果項目檔案，專案可以參考為基礎或目錄為基礎的專案。  
  
 在參考專案中，項目可以出現在多個專案。 不過，實際項目表示的檔案位於中只有一個目錄。 在目錄為基礎的專案中，所有專案項目存都在於目錄結構。  
  
 本機項目會儲存在應用程式安裝所在的相同電腦上。 遠端的項目可以儲存在本機網路中，不同的伺服器上或網際網路上其他位置。  
  
## <a name="project-file-persistence"></a>專案檔案的持續性  
 將資料儲存在一般的一般檔案系統中，或結構化儲存體？ 會使用標準編輯器中或在專案特定編輯器開啟檔案嗎？  
  
 若要保存其資料，大部分的應用程式將其資料儲存在檔案中，並讀取它時使用者必須檢閱或變更的資訊。  
  
 結構化儲存體，也稱為複合檔案，通常是在數個元件物件模型 (COM) 物件需要將其保存的資料儲存在單一檔案時使用。 結構化儲存體，使用數個不同的軟體元件可以共用單一磁碟檔案。  
  
 您有數個選項需要考慮的持續性專案中的項目。 您可以執行任何一種下列選項：  
  
-   當已經變更，分別儲存每個檔案。  
  
-   擷取在單一的許多交易**儲存**作業。  
  
-   儲存檔案在本機，然後發行至伺服器，或使用另一種方法來儲存專案項目，該項目代表遠端物件的資料連接時。  
  
 如需持續性的詳細資訊，請參閱[專案持續性](../../extensibility/internals/project-persistence.md)和[開啟和儲存的專案項目](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
## <a name="project-commitment-model"></a>專案承諾的模型  
 將保存的資料物件會開啟以直接模式或交易的模式嗎？  
  
 時資料物件會以直接的模式開啟，資料所做的變更會立即或當使用者以手動方式儲存檔案時，才會合併。  
  
 資料物件開啟時使用交易的模式，變更會儲存到記憶體中的暫存位置，並未經過認可，直到使用者手動選擇要儲存檔案。 在這段時間，必須一起出現的所有變更，或將會進行任何變更。  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [開啟並儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)   
 [專案持續性](../../extensibility/internals/project-persistence.md)   
 [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)   
 [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)   
 [建立專案類型](../../extensibility/internals/creating-project-types.md)