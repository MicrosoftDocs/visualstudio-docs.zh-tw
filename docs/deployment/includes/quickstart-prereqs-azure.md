---
ms.openlocfilehash: 3ffab1767817189c8bf27c699713354979425d21
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101750842"
---
## <a name="prerequisites"></a>必要條件

::: moniker range=">=vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)，已安裝您所選語言適用的工作負載：
  * ASP.NET：**ASP.NET 與網頁程式開發**
  * Node.js：**Node.js 開發**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)，已安裝您所選語言適用的工作負載：
  * ASP.NET：**ASP.NET 與網頁程式開發**
  * Node.js：**Node.js 開發**
::: moniker-end

* Azure 訂用帳戶。 如果您還沒有訂用帳戶，可以[免費註冊](https://azure.microsoft.com/free/dotnet/)，其中包含 30 天美金 $200 元的點數及 12 個月熱門免費服務。

* ASP.NET、ASP.NET Core、.NET Core 或 Node.js 專案。 如果您還沒有專案，請選取下列一個選項：
  * ASP.NET Core：遵循 [快速入門：使用 Visual Studio 建立您的第一個 ASP.NET Core web 應用程式](../../ide/quickstart-aspnet-core.md)，或使用下列步驟：
    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 中，選擇 [開始] 視窗中的 [ **建立新專案** ]。 如果 [開始] 視窗未開啟，請 **選擇 [** 檔案  >  **開始視窗]**。 在 [搜尋] 方塊中輸入 **web 應用程式** ，選擇 [ **c #** ] 作為 [語言]，然後選擇 [ **ASP.NET Core web 應用程式 (模型-查看控制器)**]，然後選擇 **[下一步]**。 在下一個畫面中，將專案命名為 **MyASPApp**，然後選擇 **[下一步]**。

    選擇建議的目標架構 ( .NET Core 3.1) 或 .NET 5，然後選擇 [ **建立**]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 中，**選擇 [檔案**  >  **新增專案**]，選取 [ **Visual c #**  >  **.net Core**]，然後選取 [ **ASP.NET Core Web 應用程式**]。 出現提示時，選取 [Web 應用程式 (模型-檢視-控制器)] 範本，確定已選取 [無驗證]，然後選取 [確定]。
    ::: moniker-end
  * Node.js：請遵循[快速入門：使用 Visual Studio 建立您的第一個 Node.js 應用程式](../../ide/quickstart-nodejs.md)，或者使用 [檔案][新增專案] > ，選取 [JavaScript]，然後選取 [空白的 Node.js Web 應用程式]。

* 確定您使用 [建置] > [建置方案] 功能表命令建置專案，然後遵循部署步驟。