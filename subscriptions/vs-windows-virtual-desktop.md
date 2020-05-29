---
title: Visual Studio 訂閱的 Microsoft Windows 虛擬桌面權益 |Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/20/2020
ms.topic: conceptual
description: 瞭解如何透過您的 Visual Studio 訂用帳戶來利用 Microsoft Windows 虛擬桌面
ms.openlocfilehash: b84527f7bdaf3e9218585bd52af0743ef23a5637
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183583"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>存取訂用帳戶中的 Windows 虛擬桌面 
Visual Studio 訂閱者現在可以針對 Microsoft Windows 虛擬桌面服務使用其 Azure 開發/測試個別點數。  
Windows 虛擬桌面是在雲端中執行的完整桌面和應用程式虛擬化服務。 這是唯一的虛擬桌面基礎結構（VDI），提供簡化的管理、多會話的 Windows 10、Office 365 ProPlus 的優化，以及遠端桌面服務（RDS）環境的支援。 幾分鐘內就能在 Azure 上部署及調整您的 Windows 桌面和應用程式，並取得內建的安全性與合規性功能。
以下是您在 Azure 上執行 Windows 虛擬桌面時可以執行的作業：
- 設定多工作階段的 Windows 10 部署，以提供具有延展性的完整 Windows 10
- 將 Office 365 ProPlus 虛擬化，並使其最佳化以在多使用者的虛擬案例中執行
- 提供具有免費擴充安全性更新的 Windows 7 虛擬桌面
- 將您現有的遠端桌面服務 (RDS) 和 Windows Server 桌面和應用程式帶到任何電腦
- 將桌面和應用程式虛擬化
- 透過統一的管理體驗來管理 Windows 10、Windows Server 和 Windows 7 桌上型電腦和應用程式，如需有關 Windows 虛擬桌面可執行之工作的詳細資訊，請觀看[簡介影片](https://docs.microsoft.com/azure/virtual-desktop/overview)。

## <a name="use-windows-virtual-desktop-with-azure"></a>搭配 Azure 使用 Windows 虛擬桌面 
Visual Studio 訂閱者現在有數種方式可以使用 Azure 訂用帳戶來支付 Windows 虛擬桌面服務：
- [Azure DevTest 個別信用額度](vs-azure.md)。  在訂用帳戶中收到 Azure DevTest 個別信用額度的訂閱者，可以使用這些信用額度來支付 Windows 虛擬桌面服務的費用。  每月信用額度的數量取決於訂用帳戶層級。
- [Azure DevTest 隨用隨付訂用](vs-azure-payg.md)帳戶。  您可以建立 Azure 訂用帳戶並連結付款條件，以提供順暢的方式來為您的 Windows 虛擬桌面使用量付費。 
- [Azure Enterprise 合約 DevTest 供應](azure-ea-devtest.md)專案。  透過此供應專案，具有 Enterprise 合約的訂閱者可以用折扣價支付 Azure 的 Windows 虛擬桌面費用。 

## <a name="requirements"></a>規格需求
Windows 虛擬桌面需要將聯結 Vm 的 Azure Active Directory （Azure AD）。  使用者必須是此 Azure AD 的成員。  有兩個選項可執行 Azure AD：
- Azure AD 目錄服務]。  對於大多數的使用者而言，這是更容易執行的選項。
- 執行網域控制站促銷的虛擬機器。  此選項需要更多的工作來進行設定，但可為大部分的使用者提供較低的作業成本。
若要查看使用 Windows 虛擬桌面之必要條件的完整清單，請流覽 Windows 虛擬桌面[總覽頁面](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)。 

## <a name="get-started"></a>開始使用 
當您的所有必要條件都已就緒時，您會想要完成數個動作來準備您的實施。  請參閱這些教學課程以開始使用：
- [建立 Windows 虛擬桌面租用戶](https://docs.microsoft.com/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- 使用 Azure 入口網站[建立主機集](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace)區
- [管理 Windows 虛擬桌面的應用程式群組](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups)

## <a name="eligibility"></a>資格
| 訂用帳戶層級                                                 |     聲道                                            | 優點                                                          | 可續約？    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL, Azure, 零售, | 可用|  Yes          |
| 含 GitHub Enterprise 的 Visual Studio Enterprise  | VL | 可用|  Yes          |
| Visual Studio Professional (Standard) | VL, Azure, 零售                                       | 可用                                                             |  Yes             |
| 含 GitHub Enterprise 的 Visual Studio Professional | VL                                       | 可用                                        |  Yes           |
| Visual Studio Test Professional (標準訂用帳戶)                         | VL, 零售                                              | 可用|  Yes          |
| MSDN 平台 (標準)                                          | VL, 零售                                              | 可用                                         |  Yes          |
| Visual Studio Enterprise (Standard)  | NFR<sup>1</sup> |無法使用  | 不適用 |
| Visual Studio Enterprise、Visual Studio Professional (每月雲端) | Azure | 無法使用 | 不適用 |

<sup>1</sup>  *包括：禁止轉售（NFR）、FTE、最有價值專家（MVP）、區域主管（RD）、Microsoft 合作夥伴網路（MPN）、Visual Studio 產業夥伴（VSIP）、Microsoft 認證訓練人員、BizSpark、想像*

> [!NOTE]
> Microsoft 不再於雲端訂用帳戶中提供 Visual Studio Professional 年度訂用帳戶和 Visual Studio Enterprise 年度訂用帳戶。 現有的客戶體驗，以及更新、增加、減少或取消其訂用帳戶的能力將不會改變。 建議新客戶前往以 [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) 探索 Visual Studio 購買的不同選項。

不確定您使用哪一個訂用帳戶？  連接到 [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) 以查看指派給您的電子郵件地址的所有訂用帳戶。 若沒有看到您的所有訂用帳戶，可能有一或多個訂用帳戶是指派到不同的電子郵件地址。  您必須以該電子郵件地址登入才能查看對應的訂用帳戶。

## <a name="see-also"></a>另請參閱
- [Azure 文件](https://docs.microsoft.com/azure/)
- [Windows 虛擬桌面文件](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>後續步驟
-   如果您需要購買 Visual Studio 訂用帳戶，請參閱：
     - 透過 Microsoft Store[零售購買的定價](https://visualstudio.microsoft.com/vs/pricing/)
     - [大量授權方案](https://www.microsoft.com/licensing/default)
-   深入瞭解[Windows 虛擬桌面](https://docs.microsoft.com/azure/virtual-desktop/overview) 
