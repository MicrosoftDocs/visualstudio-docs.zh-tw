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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1cf4a809c1353f2fe30383a312f65b6c623083db
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925676"
---
# <a name="configure-service-reference-dialog-box"></a>設定服務參考對話方塊

[**設定服務參考**] 對話方塊可讓您設定 WINDOWS COMMUNICATION FOUNDATION (WCF) 服務的行為。

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

更新服務參考在其中尋找服務的網址。 例如, 在開發期間, 服務可能會裝載在開發伺服器上, 並于稍後移至實際伺服器, 強制位址變更。

> [!NOTE]
> 從 [新增服務參考對話方塊] 顯示 [設定服務參考] 對話方塊時，無法使用位址項目。

**產生的類別存取層級**

判斷 WCF 用戶端類別的程式碼存取層級。

> [!NOTE]
> 針對網站專案，這個選項一律會設為 `Public`，而且無法變更。 如需詳細資訊，請參閱[針對服務參考進行疑難排解](../data-tools/troubleshooting-service-references.md)。

**產生非同步作業**

判斷 WCF 服務方法是以同步方式呼叫 (預設值), 還是以非同步方式呼叫。

**產生以工作為基礎的作業**

撰寫非同步程式碼時, 這個選項可讓您利用 .NET 4 引進的工作平行程式庫 (TPL)。 請參閱工作[平行程式庫 (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)。

**總是產生訊息合約**

判斷是否為 WCF 用戶端產生訊息合約類型。 如需訊息合約的詳細資訊，請參閱[使用訊息合約](/dotnet/framework/wcf/feature-details/using-message-contracts)。

**集合類型**

指定 WCF 用戶端的清單集合類型。 預設類型為 <xref:System.Array>。

**字典集合類型**

指定 WCF 用戶端的字典集合類型。 預設類型為 <xref:System.Collections.Generic.Dictionary%602>。

**重複使用參考組件中的類型**

判斷 WCF 用戶端是否嘗試重複使用已存在於所參考元件中的內容, 而不是在新增或更新服務時產生新的類型。 預設會核取這個選項。

**重複使用所有參考組件中的類型**

選取時, 會盡可能重複使用**參考元件清單**中的所有類型。 根據預設，這個選項是選取的。

**重複使用指定參考組件中的類型**

選取時, 只會重複使用 [**參考的元件] 清單**中選取的類型。

**參考組件清單**

包含專案或網站之參考元件的清單。 當您選取 [**重複使用指定的參考元件中的類型**] 時, 可以選取或清除個別元件。

**新增 Web 參考**

顯示 [新增 Web 參考] 對話方塊。

> [!NOTE]
> 此選項只應用於以 .NET Framework 2.0 版為目標的專案。
>
> [!NOTE]
> [**加入 Web 參考**] 按鈕僅適用于從 [**加入服務參考] 對話方塊**顯示 [**設定服務參考**] 對話方塊時。

## <a name="see-also"></a>另請參閱

- [如何：新增 web 服務的參考](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/configure-service-reference-dialog-box.md)