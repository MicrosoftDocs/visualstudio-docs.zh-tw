---
redirect_url: /visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio
ms.openlocfilehash: 5ba8ada294275a99aab27ff9c249d6c3d8e17da3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
標題: 「 繫結 Windows Form 控制項至資料 |Microsoft 文件 」 ms.custom:""ms.date:"11/04/2016"ms.reviewer 會:""ms.suite:""ms.tgt_pltfrm:""ms.topic: 「 發行項"helpviewer_keywords: 
  - 「 顯示資料，將 Windows Form 控制項 」
  - 「 Windows 表單顯示資料 」，
  - 「 資料來源，顯示 」
  - 「 資料 [Windows Form]，顯示 」 ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21 caps.latest.revision: 28 作者:"gewarren"ms.author:"gewarren"管理員： ghogen ms.technology: [vs-資料-工具]
---
# <a name="bind-windows-forms-controls-to-data"></a>Windows Form 控制項繫結至資料
您可以將物件從資料來源繫結至控制項**資料來源**視窗拖曳至 Windows Form 或拖曳至表單上現有的控制項。 您拖曳項目之前，您可以設定您想要繫結至控制項的類型。 根據您選擇本身，或個別的資料行的資料表會出現不同的值。  您也可以設定自訂值。 [詳細資料] 資料表，表示每個資料行的繫結至個別的控制項。  

![資料來源繫結至 DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "DataGridView raddata 繫結資料來源")  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>繫結至 DataGridView 控制項中的資料  
針對 DataGridView，整份資料表繫結至該單一的控制項。 當您將 DataGridView 拖曳至表單時，工具帶狀用於巡覽資料錄 (<xref:System.Windows.Forms.BindingNavigator>) 也會出現。 A[資料集](../data-tools/dataset-tools-in-visual-studio.md)， [TableAdapter](../data-tools/create-and-configure-tableadapters.md)， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>出現在元件匣中。 在下圖中，因為客戶資料表 Orders 資料表的關聯性，也會加入 TableAdapterManager。 這些變數是所有宣告在自動產生程式碼為表單類別中的私用成員。 自動產生的程式碼，以便填滿 DataGridView 位於 form_load 事件處理常式。 儲存更新的資料庫資料的程式碼位於 BindingNavigator 儲存事件處理常式。 您可以移動，或視需要修改這個程式碼。  
  
 ![GridView BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView BindingNavigator")  
  
 您可以自訂和行為的 DataGridView BindingNavigator 上的每個右角的智慧標籤，即可：  
  
 ![DataGridView 和繫結導覽智慧標籤](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView 和繫結導覽智慧標籤")  
  
 如果控制項應用程式需求不是可從**資料來源**視窗中，您可以將控制項。 如需詳細資訊，請參閱[將自訂控制項加入至資料來源視窗](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
 您也可以拖曳項目從**資料來源**視窗拖曳至表單，以將控制項繫結至資料上的控制項。 已繫結至資料的控制項已的資料繫結重設為最近拖曳至其本身的項目。 若要有效置放目標，控制項必須是可顯示基礎資料類型的項目拖曳到從**資料來源**視窗。 例如，不能將具有資料類型的項目拖曳<xref:System.DateTime>到<xref:System.Windows.Forms.CheckBox>，因為<xref:System.Windows.Forms.CheckBox>不是可顯示日期。  
  
## <a name="bind-to--data-in-individual-controls"></a>繫結至個別控制項中的資料  
 當您將資料來源繫結至 [詳細資料] 會在資料集中的每個資料行繫結至個別的控制項。  
  
 ![資料來源繫結詳細資料](../data-tools/media/raddata-bind-data-source-to-details.png "raddata 繫結資料來源詳細資料")  
  
> [!IMPORTANT]
>  請注意，在上圖中，您將從 Customers 資料表中，不是從 「 訂單 」 資料表中的 [訂單] 屬性。 繫結至 Customer.Orders 屬性，在 DataGridView 中進行巡覽命令會立即反映在詳細資料控制項。 如果您拖曳 Orders 資料表中，控制項仍然會繫結至資料集，但沒有它們就不會同步 DataGridView。  
  
 下圖顯示預設資料繫結控制項的 Customers 資料表中的 Orders 屬性繫結至 [詳細資料] 之後才加入至表單中**資料來源**視窗。  
  
 ![Orders 資料表繫結至詳細資料](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata Orders 資料表繫結至詳細資料")  
  
 請注意每個控制項具有智慧標籤。 這個標記可讓該控制項只會套用的自訂項目。  
  
## <a name="see-also"></a>另請參閱  
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)