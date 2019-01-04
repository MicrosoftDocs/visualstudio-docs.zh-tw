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
ms.openlocfilehash: f421874e092ff4d0d6e722b7bebee6f6bb48f7ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842443"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>事件處理常式傳播模型外的變更

在 Visualization and Modeling SDK，您可以定義存放區的事件處理常式，以將變更傳播到外部存放區，例如非存放區變數、 檔案、 在其他存放區或其他 Visual Studio 擴充功能中的模型的資源。 存放區事件處理常式會觸發事件發生在交易結束之後執行。 它們也會在復原或取消復原作業中執行。 因此，不同於存放區規則存放區事件是最適合用來更新值以外的存放區中。 不同於.NET 事件存放區事件處理常式會註冊要接聽的類別： 您沒有註冊個別的處理常式，每個執行個體。 如需如何選擇不同的方式來處理變更的詳細資訊，請參閱[回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)。

在圖形化介面和其他使用者介面控制項是可由存放區事件的外部資源的範例。

### <a name="to-define-a-store-event"></a>若要定義的存放區事件

1.  選擇您想要監視的事件類型。 如需完整清單，查看 屬性<xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>。 每個屬性會對應至類型的事件。 最常使用的事件類型包括：

    -   `ElementAdded` -觸發模型項目時，關聯性連結、 圖形或連接器建立。

    -   ElementPropertyChanged-觸發時的值`Normal`網域屬性會變更。 只有當新的和舊的值不相等，則會觸發事件。 事件不能用於計算及自訂的儲存體屬性。

         它無法套用至角色內容對應至關聯性連結。 請改用`ElementAdded`来監視的網域關聯性。

    -   `ElementDeleted` -觸發模型項目之後，關聯性、 圖形或連接器已刪除。 您仍然可以存取屬性值的項目，但會有其他項目沒有關聯性。

2.  加入的部分類別定義_您的 Dsl_**DocData**不同的程式碼檔案裡**DslPackage**專案。

3.  事件的程式碼撰寫的方法，如下列範例所示。 它可以是`static`，除非您想要存取`DocData`。

4.  覆寫`OnDocumentLoaded()`登錄處理常式。 如果您有多個處理常式時，您可以註冊它們全都放在相同的位置。

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

存放區並不正常使用事件來傳播變更在存放區，因為事件處理常式執行認可交易之後。 相反地，您會使用存放區的規則。 如需詳細資訊，請參閱 <<c0> [ 規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。

不過，您可以使用事件處理常式存放區，讓其他的更新，如果您想讓使用者能夠復原分開原始事件的其他更新。 例如，假設小寫字元會專輯標題的一般慣例。 您可以撰寫會更正為小寫的標題之後使用者已輸入大寫, 的存放區事件處理常式。 但是，使用者可以使用 [復原] 命令來取消您的修正，還原的大寫字元。 第二個復原會移除使用者的變更。

相較之下，如果您撰寫 store 規則，以執行相同的動作，使用者的變更與您的修正會在相同交易中，如此使用者無法復原的調整，而不會遺失原始的變更。

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

-   使用`store.InUndoRedoOrRollback`若要避免變更模型中復原的項目。 交易管理員會設定所有項目回到其原始狀態存放區中。

-   使用`store.InSerializationTransaction`若要避免從檔案載入模型時變更。

-   您的變更會導致進一步觸發的事件。 請確定您避免無限迴圈。

## <a name="store-event-types"></a>儲存事件類型

每個事件類型會對應至 Store.EventManagerDirectory 中的集合。 您可以新增或移除事件處理常式在任何時間，但通常會將它們加入文件載入時。

|`EventManagerDirectory` 屬性名稱|執行時|
|-|-|
|ElementAdded|建立網域類別、 網域關聯性、 圖形、 連接線或圖表的執行個體。|
|ElementDeleted|模型項目已從存放區的項目目錄，並不再是來源或目標的任何關聯性。 項目實際上不會從記憶體刪除，但會保留未來的復原時。|
|ElementEventsBegun|叫用為外部交易的結尾。|
|ElementEventsEnded|已處理所有其他事件時叫用。|
|ElementMoved|已從一個存放區的資料分割移至另一個模型項目。<br /><br /> 這不被與形狀圖上的位置。|
|ElementPropertyChanged|網域屬性的值已變更。 這是在舊和新值不相等時，才執行。|
|RolePlayerChanged|其中一個關聯性的兩個角色 （端點） 會參考新的項目。|
|RolePlayerOrderChanged|中的角色多重性大於 1，已變更的連結順序。|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>另請參閱

- [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)
- [範例程式碼：電路圖表](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]