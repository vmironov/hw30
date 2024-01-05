# Homework #30
1. Helm Chart в директории hw30
  Run: $ cd hw30/; helm install hw30 ./

2. Postman collection
  Run: newman run HW30.postman_collection.json
  
  
# Краткое описание

Сделано 4 сервиса:
1. Warehouse - отвечает за резервирование\удаление резерва товара на складе
2. Payment - отвечает за прием\возврат платежа
3. Delivery - содержит 1 операцию для заказа доставки на указанное время
4. Ordering - бизнес-логика, сам процесс заказа, осуществляет оркестрацию вызовов Warehouse, Payment, Delivery. Для обработки ошибок использовалась сага - в случае ошибки отрабатывает компенсационный скоуп, который определяет по контексту текущее состояние процесса и производит компенсационные действия.

В Postman-коллекции приведено 3 сценария:
1. Успешный, когда ничего не мешает создать заказ
2. Неуспешный, когда повторно пытаемся зарезервировать товар, в этом случае происходит возврат средств.
3. Неуспешный, когда слот доставки занят, в этом случае происходит возврат средств и снятие резерва на товар.
