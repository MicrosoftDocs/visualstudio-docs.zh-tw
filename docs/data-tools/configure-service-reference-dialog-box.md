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
ms.openlocfilehash: f1b2c37f551bf7b5e0a781b91420881c594ade68
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180460"
---
# <a name="configure-service-reference-dialog-box"></a>設定服務參考對話方塊

**設定服務參考**對話方塊可讓您設定 Windows Communication Foundation (WCF) 服務的行為。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

若要存取**設定服務參考**] 對話方塊中，以滑鼠右鍵按一下服務參考中**方案總管**，然後選擇 [**設定服務參考**。 您也可以存取對話方塊中，依序按一下**進階**按鈕**加入服務參考對話方塊**。

## <a name="task-list"></a>工作清單

- 若要變更裝載 WCF 服務的位址，請輸入中的新地址**地址**欄位。

- 若要變更存取層級，WCF 用戶端中的類別，選取 存取層級關鍵字**存取產生的類別層級**清單。

- 若要以非同步方式呼叫 WCF 服務的方法，請選取**產生非同步作業**核取方塊。

- 若要在 WCF 用戶端產生訊息合約型別，請選取**總是產生訊息合約**核取方塊。

- 若要指定 WCF 用戶端的清單或字典集合類型，請選取 從型別**集合型別**並**字典集合類型**列出。

- 若要停用類型共用，請清除**重複使用參考組件中的型別**核取方塊。 若要啟用類型共用的參考組件的子集，請選取**重複使用參考組件中的型別**核取方塊，選取**重複使用指定的參考組件中的型別**，並選取所需中的參考**參考組件清單**。

## <a name="uielement-list"></a>UIElement 清單

 **地址**

 更新服務參考服務的尋找位置的 web 位址。 比方說，在開發期間，服務可能會裝載程式開發伺服器上，然後稍後移到實際執行伺服器，並強迫變更位址。

> [!NOTE]
> 位址 項目時不可以使用**設定服務參考** 對話方塊會顯示從**加入服務參考對話方塊**。

 **產生的類別的存取層級**

 判斷 WCF 用戶端類別的程式碼存取層級。

> [!NOTE]
> 針對網站專案，這個選項一律會設為 `Public`，而且無法變更。 如需詳細資訊，請參閱 <<c0> [ 疑難排解服務參考](../data-tools/troubleshooting-service-references.md)。

 **產生非同步作業**

 決定是否要以同步方式呼叫 WCF 服務方法 （預設值） 或非同步的方式。

 **產生以工作為基礎的作業**

 撰寫非同步程式碼，此選項可讓您充分利用的 Task Parallel Library (TPL) 導入.NET 4。 請參閱[工作平行程式庫 (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)。

 **總是產生訊息合約**

 決定是否在 WCF 用戶端產生訊息合約型別。 如需有關訊息合約的詳細資訊，請參閱[使用訊息合約](/dotnet/framework/wcf/feature-details/using-message-contracts)。

 **集合類型**

 指定 WCF 用戶端的清單集合類型。 預設類型為 <xref:System.Array>。

 **字典集合類型**

 指定 WCF 用戶端的字典集合類型。 預設類型為 <xref:System.Collections.Generic.Dictionary%602>。

 **重複使用參考組件中的類型**

 決定是否 WCF 用戶端會嘗試重複使用已存在於參考的組件，而不是新增或更新服務時，產生新的型別。 預設會核取這個選項。

 **重複使用所有參考的組件中的類型**

 選取時中的所有型別**參考組件清單**盡可能重複使用。 根據預設，這個選項是選取的。

 **重複使用指定的參考組件中的類型**

 選取時，只選取中的型別**參考組件清單**會重複使用。

 **參考組件清單**

 包含一份參考組件的專案或網站。 當您選取**重複使用指定的參考組件中的型別**，您可以選取或清除個別組件。

 **加入 Web 參考**

 顯示**加入 Web 參考** 對話方塊。

> [!NOTE]
> 此選項只可用於 2.0 版為目標的專案[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。

> [!NOTE]
> **加入 Web 參考** 按鈕時，才可用**設定服務參考**對話方塊隨即出現從**Add Service Reference Dialog Box**。

## <a name="see-also"></a>另請參閱

- [如何： 將參考加入至 web 服務](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/configure-service-reference-dialog-box.md)