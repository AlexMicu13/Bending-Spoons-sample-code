# Bending-Spoons-sample-code
```
  JSON_Value *value = json_value_init_object();
  JSON_Object *object = json_value_get_object(value);

  printf("username: ");
  fgets(username, BUFLEN, stdin);
  remove_newline(username);
  json_object_set_string(object, "username", username);

  printf("password: ");
  fgets(password, BUFLEN, stdin);
  remove_newline(username);
  json_object_set_string(object, "password", password);

  payload[0] = json_serialize_to_string_pretty(value);

  message = compute_post_request(IP, REGISTER_PATH, PAYLOAD_TYPE, payload, ONE,
                                 NULL, 0, NULL);
  send_to_server(sockfd, message);
  response = receive_from_server(sockfd);

  if (!verify_error(response))
    puts("Successfully registered!");

  json_value_free(value);
  json_free_serialized_string(payload[0]);
```
