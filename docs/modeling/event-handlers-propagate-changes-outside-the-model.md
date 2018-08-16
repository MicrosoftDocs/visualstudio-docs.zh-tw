---
title: 事件處理常式傳播模型外的變更
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ac748cae6bf36a95b95c5d9a27aa9469ae440eed
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953628"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>事件處理常式傳播模型外的變更

在 Visualization and Modeling SDK，您可以定義存放區將變更傳播至儲存區，例如非存放區變數、 檔案、 模型中其他存放區，或其他外部資源的事件處理常式[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]擴充功能。 儲存的事件處理常式會執行觸發的事件發生所在的交易結束之後。 它們也會在復原或取消復原作業中執行。 因此，不同於存放區規則存放區事件是最適合用於更新儲存區以外的值中。 不同於.NET 事件存放區的事件處理常式已登錄到接聽的類別： 您沒有註冊個別的處理常式，每個執行個體。 如需如何選擇不同的方式處理變更的詳細資訊，請參閱[回應和傳播變更](../modeling/responding-to-and-propagating-changes.md)。

圖形化介面和其他使用者介面控制項是可由存放區的事件處理的外部資源的範例。

### <a name="to-define-a-store-event"></a>若要定義存放區事件

1.  選擇您想要監視的事件類型。 如需完整清單，看看的屬性<xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>。 每個屬性會對應至事件的類型。 最常使用的事件類型：

    -   `ElementAdded` -觸發模型項目時，關聯性連結、 圖形或連接器建立。

    -   ElementPropertyChanged-時觸發的值`Normal`變更定義域屬性。 只有當新的和舊的值不相等，則觸發事件。 事件無法套用至導出和自訂的儲存體屬性。

         它無法套用至角色屬性的對應關聯性的連結。 請改用`ElementAdded`来監視的網域關聯性。

    -   `ElementDeleted` -觸發模型項目之後，關聯性、 圖形或連接器已刪除。 您仍然可以存取屬性值的項目，但有其他項目的任何關聯性。

2.  加入的部分類別定義*YourDsl * * * DocData** 的不同程式碼檔案中**DslPackage**專案。

3.  事件的程式碼撰寫為一種方法，如下列範例所示。 它可以是`static`，除非您想要存取`DocData`。

4.  覆寫`OnDocumentLoaded()`登錄處理常式。 如果您有多個處理常式，您可以完全在同一個位置中進行註冊。

註冊程式碼的位置並不重要。 `DocView.LoadView()` 是替代的位置。

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

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>使用事件來進行存放區中的可復原的調整

存放區並不正常使用事件針對傳播變更內部存放區，因為事件處理常式執行認可交易之後。 相反地，您會使用規則存放區。 如需詳細資訊，請參閱[規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。

不過，您可以使用事件處理常式可讓存放區，其他的更新，如果您想讓使用者能復原分開原始事件的其他更新。 例如，假設小寫字元都是專輯標題的一般慣例。 您可以撰寫使用者已輸入大寫之後更正為小寫標題的存放區事件處理常式。 但是，使用者無法使用 [復原] 命令來取消您的更正，還原大寫字元。 第二個復原會移除使用者的變更。

相反地，如果您撰寫的市集規則執行相同的動作，使用者的變更與您的更正將在相同交易中，使使用者無法復原的調整，而不會遺失原始變更。

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

如果您寫入更新存放區的事件：

-   使用`store.InUndoRedoOrRollback`若要避免變更模型項目中復原。 交易管理員會設定回其原始狀態存放區中的所有項目。

-   使用`store.InSerializationTransaction`若要避免從檔案載入模型時變更。

-   您的變更會導致進一步觸發的事件。 請確定您避免無限迴圈。

## <a name="store-event-types"></a>儲存事件類型

每個事件類型會對應至 Store.EventManagerDirectory 中的集合。 您可以新增或移除事件處理常式，在任何時間，但通常會將文件載入時將其加入。

|`EventManagerDirectory` 屬性名稱|執行時|
|-------------------------------------------|-------------------|
|ElementAdded|建立領域類別、 網域關聯性、 圖形、 連接器或圖表的執行個體。|
|ElementDeleted|將模型項目已從存放區的項目目錄中移除，且不會再來源或目標的任何關聯性。 項目實際上不會從記憶體中，刪除，但未來復原時保留。|
|ElementEventsBegun|叫用為外部交易的結尾。|
|ElementEventsEnded|已處理所有其他事件時叫用。|
|ElementMoved|將模型項目已從一個存放區的磁碟分割移到另一個。<br /><br /> 這不被與圖形在圖表上的位置。|
|ElementPropertyChanged|網域屬性的值已變更。 這不會執行舊的和新的值不相等。|
|RolePlayerChanged|其中一個關聯性的兩個角色 （端點） 會參考新的項目。|
|RolePlayerOrderChanged|在角色中多重性大於 1，已變更的連結順序。|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>另請參閱

- [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)
- [範例程式碼： 循環圖表](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]