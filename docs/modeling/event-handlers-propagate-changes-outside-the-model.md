---
title: 事件處理常式傳播模型外的變更
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f35c94004a76e5671585969686798c38e5f750e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747555"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>事件處理常式傳播模型外的變更

在視覺化和模型 SDK 中，您可以定義存放區事件處理常式，以將變更傳播至存放區外部的資源，例如非存放區變數、檔案、其他儲存區中的模型，或其他 Visual Studio 延伸模組。 存放區事件處理常式會在發生觸發事件的交易結束之後執行。 它們也會在復原或重做作業中執行。 因此，與存放區規則不同的是，儲存事件最適合用來更新存放區以外的值。 不同于 .NET 事件，儲存事件處理常式會註冊以接聽類別：您不需要為每個實例註冊個別的處理常式。 如需如何在不同的處理變更方式之間進行選擇的詳細資訊，請參閱[回應和傳播變更](../modeling/responding-to-and-propagating-changes.md)。

圖形介面和其他使用者介面控制項是可由存放區事件處理的外部資源範例。

### <a name="to-define-a-store-event"></a>若要定義存放區事件

1. 選擇您想要監視的事件種類。 如需完整清單，請查看 <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> 的屬性。 每個屬性都會對應到一個事件種類。 最常使用的事件種類為：

    - `ElementAdded`-在建立模型專案、關聯性連結、圖形或連接器時觸發。

    - ElementPropertyChanged-當 `Normal` 網域屬性的值變更時觸發。 只有新的和舊的值不相等時，才會觸發事件。 事件不能套用至計算和自訂儲存體屬性。

         它無法套用到對應至關聯性連結的角色屬性。 相反地，請使用 `ElementAdded` 來監視網域關聯性。

    - `ElementDeleted`-已刪除模型元素、關聯性、圖形或連接器之後觸發。 您仍然可以存取元素的屬性值，但它不會與其他專案有任何關聯性。

2. 在**DslPackage**專案的個別程式碼檔案中，新增_dsl_**DocData**的部分類別定義。

3. 將事件的程式碼撰寫為方法，如下列範例所示。 除非您想要存取 `DocData`，否則可以 `static`。

4. 覆寫 `OnDocumentLoaded()` 以註冊處理常式。 如果您有一個以上的處理常式，則可以在相同的位置全部註冊。

註冊程式碼的位置並不重要。 `DocView.LoadView()` 是替代位置。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don't forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }
}
```

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>使用事件在存放區中進行可撤銷的調整

存放區事件通常不會用來傳播存放區內的變更，因為事件處理常式會在交易認可後執行。 相反地，您會使用存放區規則。 如需詳細資訊，請參閱[規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。

不過，如果您想要讓使用者能夠從原始事件分別復原額外的更新，您可以使用事件處理常式來對存放區進行額外的更新。 例如，假設小寫字元是專輯標題的一般慣例。 您可以撰寫存放區事件處理常式，在使用者以大寫輸入之後，將標題更正為小寫。 但是使用者可以使用 [復原] 命令來取消更正，以還原大寫的字元。 第二次復原會移除使用者的變更。

相反地，如果您已撰寫存放區規則來執行相同的動作，使用者的變更和更正將會在相同的交易中，讓使用者無法復原調整，而不會遺失原始變更。

```csharp
partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}
```

如果您撰寫的事件會更新存放區：

- 請使用 `store.InUndoRedoOrRollback` 來避免在復原中變更模型專案。 交易管理員會將存放區中的所有專案設定回其原始狀態。

- 使用 `store.InSerializationTransaction`，以避免在從檔案載入模型時進行變更。

- 您的變更將會觸發進一步的事件。 請確定您避免無限迴圈。

## <a name="store-event-types"></a>儲存事件種類

每個事件種類都會對應到 EventManagerDirectory 中的集合。 您可以隨時新增或移除事件處理常式，但在載入檔時通常會加入它們。

|`EventManagerDirectory` 屬性名稱|執行時機|
|-|-|
|ElementAdded|系統會建立網域類別、網域關聯性、圖形、連接器或圖表的實例。|
|ElementDeleted|已從存放區的元素目錄中移除模型專案，而且不再是任何關聯性的來源或目標。 專案實際上不會從記憶體中刪除，但會在未來復原時保留。|
|ElementEventsBegun|在外部交易結束時叫用。|
|ElementEventsEnded|當所有其他事件都已處理時叫用。|
|ElementMoved|已將模型專案從一個存放區分割移到另一個。<br /><br /> 這與圖表上圖形的位置無關。|
|ElementPropertyChanged|網域屬性的值已變更。 只有當舊值和新值不相等時，才會執行此工作。|
|RolePlayerChanged|關聯性的兩個角色（end）其中之一會參考新的元素。|
|RolePlayerOrderChanged|在多重性大於1的角色中，連結的順序已經變更。|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>請參閱

- [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)
- [範例程式碼：線路圖表](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]