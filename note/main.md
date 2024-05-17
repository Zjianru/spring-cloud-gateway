# Spring cloud gateway
Route（路由）: 网关的基本构件。它由一个ID、一个目的地URI、一个谓词（Predicate）集合和一个过滤器（Filter）集合定义。如果集合谓词为真，则路由被匹配。

Predicate（谓词）: 这是一个 Java 8 Function Predicate。输入类型是 Spring Framework ServerWebExchange。这让你可以在HTTP请求中的任何内容上进行匹配，比如header或查询参数。

Filter（过滤器）: 这些是 GatewayFilter 的实例，已经用特定工厂构建。在这里，你可以在发送下游请求之前或之后修改请求和响应。

<img src="img/SpringCloudGateway工作流程.png" alt="SpringCloudGateway工作流程">

客户端向 Spring Cloud Gateway 发出请求。如果Gateway处理程序映射确定一个请求与路由相匹配，它将被发送到Gateway Web处理程序。这个处理程序通过一个特定于该请求的过滤器链来运行该请求。过滤器被虚线分割的原因是，过滤器可以在代理请求发送之前和之后运行逻辑。所有的 "pre" （前）过滤器逻辑都被执行。然后发出代理请求。在代理请求发出后，"post" （后）过滤器逻辑被运行。