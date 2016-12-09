# Chat & Realtime Data Stream

You can connect to our streaming servers for chat and realtime data. This method is recommended over polling other endpoints. Talk to the nerds for more information.

> Example Script

```html
<html>
  <script src="https://stream.derbyjackpot.com/chat.js"></script>
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>
  <script type="text/javascript">
    var client = new Faye.Client('https://stream.derbyjackpot.com/chat');

    auth_extension = {
      outgoing: function(message, callback) {
        // on every outgoing message, attach the auth token
        message['ext'] = {
          auth_token: "F7VwDj2iw089TJLcLrRO9C6Gz8uVgHUGMftCGGipbJvazZjXVh663UZTTf78Mav0QjKRxTWsgIN89PJNJ14A3IlWeAxMajdzd6iL"
        };
        return callback(message);
      }
    };

    client.addExtension(auth_extension);

    var subscription = client.subscribe('/feed/v1/touchtunes', function(message) {
      // handle message
      console.log(message);

      txt = '';
      if (message['type'] == 'wager') {
        user = message['user']['screen_name'] + "<img height=30 width=30 src='" + message['user']['image_url'] + "'>"
        txt = user + " just wagered " + message['amount'];
      }

      if (message['type' == 'win']) {
        txt = user + " won " + message['net_payoff_amount'];
      }

      if (message['type'] == 'race') {
        txt = "Race " + message['name'] + " " + message['race_number'] + " changed.";
      }

      $("#content").append("<div>" + txt + "</div>");
    });
  </script>

  <body>
    <div id="content"></div>
  </body>
</html>
```
