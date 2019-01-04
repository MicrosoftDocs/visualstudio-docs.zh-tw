---
title: CA3147:使用 ValidateAntiForgeryToken 標示動詞處理常式
ms.date: 08/08/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 96660dfe1de6b4fb2490bd00b7ce408d0548ba67
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954694"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147:使用 ValidateAntiForgeryToken 標示動詞處理常式

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

ASP.NET MVC 控制器動作方法不與標示[ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108(v=vs.118))，或指定的 HTTP 指令動詞，例如屬性[HttpGetAttribute](/previous-versions/aspnet/web-frameworks/ee470993(v%3dvs.118))或[AcceptVerbsAttribute](/previous-versions/aspnet/web-frameworks/dd470553%28v%3dvs.118%29)。

## <a name="rule-description"></a>規則描述

當設計 ASP.NET MVC 控制器，請留意跨網站偽造要求攻擊。 跨網站要求偽造攻擊可以從已驗證的使用者傳送惡意要求到您的 ASP.NET MVC 控制站。 如需詳細資訊，請參閱 < [ASP.NET MVC 和 web 網頁中的 XSRF/CSRF 防護](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages)。

此規則會檢查該 ASP.NET MVC 控制器動作方法可能是：

- 已[ValidateAntiforgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108%28v%3dvs.118%29)並指定允許的 HTTP 動詞命令，不包括 HTTP GET。

- 指定 HTTP GET 為允許的動詞命令。

## <a name="how-to-fix-violations"></a>如何修正違規

- 適用於 ASP.NET MVC 控制器動作，以處理 HTTP GET 要求，並不會有潛在危險的副作用，新增[HttpGetAttribute](/previous-versions/aspnet/web-frameworks/ee470993%28v%3dvs.118%29)方法。

   如果您有 ASP.NET MVC 控制器動作，以處理 HTTP GET 要求，並具有例如修改機密資料可能會造成損害的副作用，您的應用程式是容易遭受跨網站偽造要求攻擊。  您必須重新設計應用程式，因此只有 HTTP POST、 PUT 或 DELETE 要求執行敏感性作業。

- 適用於 ASP.NET MVC 控制器動作處理 HTTP POST、 PUT 或 DELETE 要求，新增[ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108(v=vs.118))並指定允許的 HTTP 動詞命令的屬性 ([AcceptVerbsAttribute](/previous-versions/aspnet/web-frameworks/dd470553%28v%3dvs.118%29)[HttpPostAttribute](/previous-versions/aspnet/web-frameworks/ee264023%28v%3dvs.118%29)， [HttpPutAttribute](/previous-versions/aspnet/web-frameworks/ee470909%28v%3dvs.118%29)，或[HttpDeleteAttribute](/previous-versions/aspnet/web-frameworks/ee470917%28v%3dvs.118%29))。 此外，您必須呼叫[HtmlHelper.AntiForgeryToken()](/previous-versions/aspnet/web-frameworks/dd504812%28v%3dvs.118%29)從您的 MVC 檢視或 Razor 網頁的方法。 如需範例，請參閱[檢查編輯方法與編輯檢視](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告，如果：

- ASP.NET MVC 控制器動作有沒有會造成損害的副作用。

- 應用程式會驗證 antiforgery 權杖，以不同方式。

## <a name="validateantiforgerytoken-attribute-example"></a>ValidateAntiForgeryToken 屬性範例

### <a name="violation"></a>違規

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            // You don't want an attacker to specify to who and how much money to transfer.

            return null;
        }
    }
}
```

### <a name="solution"></a>方案

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            return null;
        }
    }
}
```

## <a name="httpget-attribute-example"></a>HttpGet 屬性範例

### <a name="violation"></a>違規

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult Help(int topicId)
        {
            // This Help method is an example of a read-only operation with no harmful side effects.
            return null;
        }
    }
}
```

### <a name="solution"></a>方案

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpGet]
        public ActionResult Help(int topicId)
        {
            return null;
        }
    }
}
```
