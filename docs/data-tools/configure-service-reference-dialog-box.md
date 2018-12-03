---
title: 設定服務參考對話方塊
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f0cb2737356813a9b637d7f16e9d5cda704c022a
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389496"
---
# <a name="configure-service-reference-dialog-box"></a>設定服務參考對話方塊

**設定服務參考**對話方塊可讓您設定 Windows Communication Foundation (WCF) 服務的行為。

若要存取 [設定服務參考] 對話方塊，請以滑鼠右鍵按一下 [方案總管] 中的服務參考，然後選擇 [設定服務參考]。 您也可以按一下 [新增服務參考對話方塊] 中的 [進階] 按鈕來存取這個對話方塊。

## <a name="task-list"></a>工作清單

- 若要變更裝載 WCF 服務的位址，請在 [位址] 欄位中輸入新位址。

- 若要變更 WCF 用戶端中的類別存取層級，請在 [產生的類別存取層級] 清單中選取存取層級關鍵字。

- 若要以非同步方式呼叫 WCF 服務的方法，請選取 [產生非同步作業] 核取方塊。

- 若要產生 WCF 用戶端的訊息合約類型，請選取 [總是產生訊息合約] 核取方塊。

- 若要指定 WCF 用戶端的清單或字典集合類型，請從 [集合類型] 和 [字典集合類型] 清單中選取類型。

- 若要停用類型共用，請清除 [重複使用參考組件中的類型] 核取方塊。 若要針對參考組件的子集啟用類型共用，請選取 [重複使用參考組件中的類型] 核取方塊，然後選取 [重複使用指定的參考組件中的類型]，再從 [參考組件清單] 中選取所需的參考。

## <a name="uielement-list"></a>UIElement 清單

 **位址**

 更新服務參考服務的尋找位置的 web 位址。 比方說，在開發期間，服務可能會裝載程式開發伺服器上，然後稍後移到實際執行伺服器，並強迫變更位址。

> [!NOTE]
> 從 [新增服務參考對話方塊] 顯示 [設定服務參考] 對話方塊時，無法使用位址項目。

 **產生的類別存取層級**

 判斷 WCF 用戶端類別的程式碼存取層級。

> [!NOTE]
> 針對網站專案，這個選項一律會設為 `Public`，而且無法變更。 如需詳細資訊，請參閱[針對服務參考進行疑難排解](../data-tools/troubleshooting-service-references.md)。

 **產生非同步作業**

 決定是否要以同步方式呼叫 WCF 服務方法 （預設值） 或非同步的方式。

 **產生以工作為基礎的作業**

 撰寫非同步程式碼，此選項可讓您充分利用的 Task Parallel Library (TPL) 導入.NET 4。 請參閱[工作平行程式庫 (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)。

 **總是產生訊息合約**

 決定是否在 WCF 用戶端產生訊息合約型別。 如需訊息合約的詳細資訊，請參閱[使用訊息合約](/dotnet/framework/wcf/feature-details/using-message-contracts)。

 **集合類型**

 指定 WCF 用戶端的清單集合類型。 預設類型為 <xref:System.Array>。

 **字典集合類型**

 指定 WCF 用戶端的字典集合類型。 預設類型為 <xref:System.Collections.Generic.Dictionary%602>。

 **重複使用參考組件中的類型**

 決定是否 WCF 用戶端會嘗試重複使用已存在於參考的組件，而不是新增或更新服務時，產生新的型別。 預設會核取這個選項。

 **重複使用所有參考組件中的類型**

 選取時中的所有型別**參考組件清單**盡可能重複使用。 根據預設，這個選項是選取的。

 **重複使用指定參考組件中的類型**

 選取時，只選取中的型別**參考組件清單**會重複使用。

 **參考組件清單**

 包含一份參考組件的專案或網站。 當您選取**重複使用指定的參考組件中的型別**，您可以選取或清除個別組件。

 **新增 Web 參考**

 顯示 [新增 Web 參考] 對話方塊。

> [!NOTE]
> 此選項只可用於 2.0 版為目標的專案[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。
>
> [!NOTE]
> **加入 Web 參考** 按鈕時，才可用**設定服務參考**對話方塊隨即出現從**Add Service Reference Dialog Box**。

## <a name="see-also"></a>另請參閱

- [如何：將參考新增至 Web 服務](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/configure-service-reference-dialog-box.md)