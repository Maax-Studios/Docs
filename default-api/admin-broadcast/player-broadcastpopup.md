# 🔵 PLAYER:broadcastPopup()

{% code title="Function" %}
```
PLAYER:broadcastPopup(text)
```
{% endcode %}

{% tabs %}
{% tab title="Arguments" %}
*   <mark style="color:blue;">**string**</mark>

    Message
{% endtab %}
{% endtabs %}

### <mark style="color:blue;">Example</mark>

{% code title="Clientside" %}
```
concommand.Add(„popup“, function(ply,cmd,args, argString)

    net.Start(„ClientBroadcast“)
    net.WriteString(argString)
    net.SendToServer()

end)
```
{% endcode %}

{% code title="Serverside" %}
```
net.Receive("ClientBroadcast", function(_,ply)

    for _,i in pairs(player.GetAll()) do 
        if !IsValid(i) then return end
        i:broadcastPopup(net.ReadString())
    end

end)
```
{% endcode %}
