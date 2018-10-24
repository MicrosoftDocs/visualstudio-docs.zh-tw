---
title: 自訂刪除行為
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: a4b3df4661b23268fed811799c80cfc31b624a50
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849147"
---
# <a name="customizing-deletion-behavior"></a>自訂刪除行為
刪除項目通常會導致相關項目也被刪除。 會刪除與它連接的所有關聯性以及任何子項目。 這種行為稱為*刪除傳播*。 您可以自訂刪除傳播以 (舉例而言) 安排刪除其他相關項目。 藉由撰寫程式碼，您可以根據模型的狀態執行刪除傳播。 您也可以促使其他變更因回應刪除而發生。

 本主題包含下列章節：

-   [預設刪除行為](#default)

-   [設定角色的 [傳播刪除] 選項](#property)

-   [覆寫刪除關閉](#closure)-使用這項技術，其中刪除可能會導致刪除相鄰項目。

-   [使用 OnDeleting 和 OnDeleted](#ondeleting) -使用這些方法在回應可能包括其他動作，例如更新值的內部或外部存放區的位置。

-   [刪除規則](#rules)-使用規則來傳播任何類型內的存放區，其中一項變更可能會導致其他人的更新。

-   [刪除事件](#rules)-將外部存放區，例如 Visual Studio 中的其他文件的更新傳播至使用市集事件。

-   [取消合併](#unmerge)-使用取消合併作業來復原將子項目連結到其父系的合併作業。

## <a name="default"></a> 預設刪除行為
 根據預設，下列規則管理刪除傳播：

-   如果刪除了某個項目，也會刪除所有內嵌的項目。 內嵌的項目為內嵌關聯性的目標，而內嵌關聯性的來源是此項目。 比方說，如果沒有從內嵌關聯性**專輯**要**歌曲**，則也會刪除特定 Album 時，所有 Song 都刪除。

     相反地，刪除 Song 卻不會刪除 Album。

-   根據預設，刪除不會沿著參考關聯性傳播。 如果有參考關聯性**ArtistPlaysOnAlbum**從**專輯**來**演出者**、 刪除 album 不會刪除任何相關的 artist，和刪除 artist 不刪除任何 album。

     不過，刪除確實會沿著某些內建關聯性傳播。 例如，刪除某個模型項目時，也會刪除它在圖表上的圖形。 項目與圖形因 `PresentationViewsSubject` 參考關聯性而彼此相關。

-   每個連接到項目 (無論位於來源或目標角色) 的關聯性都會被刪除。 位於相反角色之項目的角色屬性將不再包含刪除的項目。

## <a name="property"></a> 設定角色的 [傳播刪除] 選項
 您可以讓刪除沿著參考關聯性傳播，或是從內嵌子系傳播到其父系。

#### <a name="to-set-delete-propagation"></a>設定刪除傳播

1. 在 DSL 定義圖上選取*角色*至想要傳播刪除。 該角色由網域關聯性方塊的左側或右側線條所表示。

    例如，如果您要指定 Album 遭到刪除時，也刪除相關的 Artist，請選取連接到網域類別 Artist 的角色。

2. 在 [屬性] 視窗中，設定**傳播刪除**屬性。

3. 按 F5 並確認：

   -   刪除此關聯性的執行個體時，也會刪除位於所選角色的項目。

   -   刪除位於相反角色的項目時，將會刪除此關聯性的執行個體，而且會刪除位於此角色的相關項目。

   您也可以查看**傳播刪除**選項**DSL 詳細資料**視窗。 選取網域類別，並在 [DSL 詳細資料] 視窗中，開啟**刪除時的行為**按一下旁邊的視窗按鈕的頁面。 **傳播**選項會顯示每個關聯性的相反角色。 **刪除 Style**資料行會指出是否**傳播**選項的預設值，但它並沒有任何個別的作用。

## <a name="delete-propagation-by-using-program-code"></a>使用程式碼來刪除傳播
 DSL 定義檔案中的選項只能讓您選擇刪除是否傳播至相鄰項目。 若要實作更複雜的刪除傳播配置，可以撰寫程式碼。

> [!NOTE]
>  若要加入您的 DSL 定義中的程式碼，請建立不同的程式碼檔案中**Dsl**專案，並撰寫部分定義以擴大 Generated Code 資料夾中的類別。 如需詳細資訊，請參閱 <<c0> [ 來自訂特定領域語言撰寫的程式碼](../modeling/writing-code-to-customise-a-domain-specific-language.md)。

## <a name="closure"></a> 定義刪除關閉
 刪除作業使用類別_YourModel_**DeleteClosure**來判斷要刪除，請提供初始選擇的項目。 它重複呼叫 `ShouldVisitRelationship()` 和 `ShouldVisitRolePlayer()`，查核關聯性的圖形。 您可以覆寫這些方法。 Shouldvisitroleplayer 隨附於的身分識別的連結和位於其中一個連結的角色的項目。 它應傳回下列其中一個值：

-   **VisitorFilterResult.Yes**-應該刪除的項目，並查核器應繼續嘗試該項目的其他連結。

-   **VisitorFilterResult.DoNotCare** -應該刪除的項目，除非另一個查詢回覆應刪除。

-   **VisitorFilterResult.Never** -項目必須不會刪除，即使另一個查詢回答**是**，並查核器不應該嘗試該項目的其他連結。

```
// When a musician is deleted, delete their albums with a low rating.
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs
partial class MusicLibDeleteClosure
{
  public override VisitorFilterResult ShouldVisitRolePlayer
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)
  {
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;
    if (link != null
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)
    {
      // Count other unvisited links to the Album of this link.
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)
              .Where(linkAlbumArtist =>
                     linkAlbumArtist != link &&
                     !walker.Visited(linkAlbumArtist))
              .Count() == 0)
      {
        // Should delete this role player:
        return VisitorFilterResult.Yes;
      }
      else
        // Don't delete unless another relationship deletes it:
        return VisitorFilterResult.DoNotCare;
    }
    else
    {
      // Test for and respond to other relationships and roles here.

      // Not the relationship or role we're interested in.
      return base.ShouldVisitRolePlayer(walker, sourceElement,
             elementLink, targetDomainRole, targetRolePlayer);
    }
  }
}
```

 關閉技術可確認在刪除開始之前就已確定要刪除的項目和連結集。 查核器還會將您的關閉結果與來自模型其他部分的結果結合。

 不過，此技術假設刪除僅影響關聯性圖形中的相鄰項目：您無法使用此方法刪除模型另一個部分中的項目。 如果您要加入項目或是進行其他變更以回應刪除，則無法使用它。

## <a name="ondeleting"></a> 使用 OnDeleting 和 OnDeleted
 您可以在網域類別或網域關聯性中覆寫 `OnDeleting()` 或 `OnDeleted()`。

1. 當項目即將被刪除時會呼叫 <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A>，但是會在中斷連接其關聯性之前呼叫。 仍然可以在其他項目中來回巡覽它，而它也仍然在 `store.ElementDirectory` 中。

    如果同時刪除數個項目，在執行刪除之前，會針對它們全部呼叫 OnDeleting。

    `IsDeleting` 為 true。

2. 刪除該項目時，會呼叫 <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A>。 它會留存在 CLR 堆積中，以便在需要時執行復原，但是它已與其他項目取消連結並從 `store.ElementDirectory` 中遭到移除。 關聯性，該角色仍然參考舊的角色扮演者。`IsDeleted` 是，則為 true。

3. 當使用者在建立項目之後呼叫復原，以及在取消復原中重複提早刪除時，會呼叫 OnDeleting 和 OnDeleted。 請使用 `this.Store.InUndoRedoOrRollback` 以避免在這些情況下更新市集項目。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用異動更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。

   例如，下列程式碼會在其最後一個子系 Song 被刪除時刪除 Album：

```

// Delete the parent Album when the last Song is deleted.
// Override methods in the embedding relationship between Album and Song:
partial class AlbumHasSongs
{
  protected override void OnDeleted()
  {
    base.OnDeleted();
    // Don't perform in-store actions in undo:
    if (this.Store.InUndoRedoOrRollback) return;
    // Relationship source and target still work:
    // Don't bother if source is already on its way out:
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)
    {
      if (this.Album.Songs.Count == 0)
      {
        this.Album.Delete();
} } } }
```

 從刪除關聯性觸發經常會比從角色項目觸發有用，因為前者在項目被刪除以及關聯性本身被刪除時都適用。 然而，如果是參考關聯性，您可能需要在相關項目被刪除時 (而不是在關聯性本身被刪除時) 傳播刪除。 本範例會在最後一位參與的 Artist 被刪除時刪除 Album，但是它不會在關聯性被刪除時回應：

```
using System.Linq; ...
// Assumes a many-many reference relationship
// between Artist and Album.
partial class Artist
{
  protected override void OnDeleting()
  {
    base.OnDeleting();
    if (this.Store.InUndoRedoOrRollback) return;
    List<Album> toDelete = new List<Album>();
    foreach (Album album in this.Albums)
    {
      if (album.Artists.Where(artist => !artist.IsDeleting)
                        .Count() == 0)
      {
        toDelete.Add(album);
      }
    }
    foreach (Album album in toDelete)
    {
      album.Delete();
} } }
```

 當您對某個項目執行 <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> 時，將會呼叫 OnDeleting 和 OnDeleted。 這些方法都是永遠執行的內嵌-也就是立即之前和之後實際的刪除作業。 如果您的程式碼刪除兩個或多個項目，將會在所有項目上輪流呼叫 OnDeleting 和 OnDeleted。

## <a name="rules"></a> 刪除規則和事件
 OnDelete 處理常式的替代方法是，您可以定義刪除規則和刪除事件。

1.  **正在刪除**並**刪除**只在交易中，而不是在復原或取消復原，會觸發規則。 您可以將它們排入佇列，在進行刪除的異動結尾處執行規則。 Deleting 規則的執行一律會早於在佇列中的任何 Deleted 規則。

     請使用規則來傳播僅影響市集中項目的變更，包括關聯性、圖表項目及其屬性。 一般而言，Deleting 規則用來傳播刪除，而 Delete 規則用來建立取代項目和關聯性。

     如需詳細資訊，請參閱 <<c0> [ 規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。

2.  **刪除**存放區事件結尾的交易，叫用，並在復原或取消復原後呼叫。 因此可用來傳播刪除到外部存放區，例如檔案、 資料庫項目或 Visual Studio 中的其他物件的物件。

     如需詳細資訊，請參閱 <<c0> [ 事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

    > [!WARNING]
    >  刪除某個項目時，您可以存取其網域屬性值，但是無法巡覽關聯性連結。 不過，如果您對某個關聯性設定已刪除事件，您也可以存取原先為其角色扮演者的兩個項目。 因此，如果您想要回應模型項目的刪除，但想要存取其所連結的項目，請在關聯性，而不是模型項目的網域類別上設定刪除事件。

### <a name="example-deletion-rules"></a>Deletion 規則範例

```
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletingRule : DeletingRule
{
  public override void ElementDeleting(ElementDeletingEventArgs e)
  {
    base.ElementDeleting(e);
    // ...perform tasks to propagate imminent deletion
  }
}
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletedRule : DeleteRule
{
  public override void ElementDeleted(ElementDeletedEventArgs e)
  {
    base.ElementDeleted(e);
    // ...perform tasks such as creating new elements
  }
}

// The rule must be registered:
public partial class MusicLibDomainModel
{
  protected override Type[] GetCustomDomainModelTypes()
  {
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
    types.Add(typeof(AlbumDeletingRule));
    types.Add(typeof(AlbumDeletedRule));
    // If you add more rules, list them here.
    return types.ToArray();
  }
}
```

### <a name="example-deleted-event"></a>Deleted 事件範例

```
partial class NestedShapesSampleDocData
{
  protected override void OnDocumentLoaded(EventArgs e)
  {
    base.OnDocumentLoaded(e);
    DomainRelationshipInfo commentRelationship =
          this.Store.DomainDataDirectory
          .FindDomainRelationship(typeof(CommentsReferenceComponents));

    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));
  }

  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)
  {
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;
    Comment comment = link.Comment;
    Component component = link.Subject;
    if (comment.IsDeleted)
    {
      // The link was deleted because the comment was deleted.
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);
    }
    else
    {
      // It was just the link that was deleted - the comment itself remains.
      System.Windows.Forms.MessageBox.Show("Removed comment link to "
           + component.Name);
    }
  }
}
```

## <a name="unmerge"></a> 取消合併
 將子項目附加至其父代作業稱為*合併*。 從工具箱建立一個或一組新項目，從模型的另一個部分移動一個或一組新項目，或是從剪貼簿複製一個或一組新項目時，就會發生該動作。 除了在父系與其新子系之間建立和內嵌關聯性之外，合併作業還可以設定其他關聯性、建立輔助項目，以及在項目中設定屬性值。 合併作業封裝在項目合併指示詞 (EMD) 中。

 EMD 也封裝補充*取消合併*或`MergeDisconnect`作業。 如果您有使用合併所建構的項目叢集，而且您想要使其餘的項目保持一致的狀態，建議您使用相關聯的取消合併從中移除項目。 取消合併作業通常會使用先前的章節所述的技巧。

 如需詳細資訊，請參閱 <<c0> [ 自訂項目的建立和移動](../modeling/customizing-element-creation-and-movement.md)。

## <a name="see-also"></a>另請參閱

- [自訂複製行為](../modeling/customizing-copy-behavior.md)
- [自訂項目的建立和移動](../modeling/customizing-element-creation-and-movement.md)
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)