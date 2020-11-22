**Explores - tips from docs**  

    explore: order_items {
      join: orders {
        type: left_outer   # supportina tik: left_outer, inner, full_outer, cross
        relationship: many_to_one
        sql_on: ${order_items.order_id} = ${orders.id} AND ${orders.id} > 1000 ;;   # prideta salyga del orders id
        fields: [shipping, tax]   # optional - nurodomi konkretus laukai
      }
      join: buyers {   # jei nera from, cia rasomas view pavadinimas
        from: users   # pavyzdyje atvejis, kai tas pats view joininamas 2kart
        type: left_outer
        relationship: many_to_one
        sql_on: ${orders.buyer_id} = ${buyers.id} ;;
      }
      join: sellers {
        from: users
        type: left_outer
        relationship: many_to_one
        sql_on: ${orders.seller_id} = ${sellers.id} ;;
      }
    }

**Views - tips from docs**

Visada gerai nurodyti primary_key (naudinga agregavimams)

    dimension: id {
      type: number
      primary_key: yes
    }
 
 
