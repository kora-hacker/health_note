``` java
List<Address> list = addressService.findByAll();
```


``` java
list	ArrayList<E>  (id=116)	
	[0]	Address  (id=147)	
		addressDescript	"厚德路1号" (id=154)	
		addressName	"卫府里店" (id=156)	
		customer_id	"0375e64208bb464c94e866f2346107aa" (id=157)	
		id	"57130061-15aa-4cec-b9bf-2d048715677b" (id=160)	
	[1]	Address  (id=148)	
	[2]	Address  (id=149)	
	[3]	Address  (id=150)	
	[4]	Address  (id=151)	
```
```
Address ( 
	addressDescript,
	addressName,
	customer_id,
	id
 );
```



CustomerMobileAction.java
```java
package com.alpha.health.customer.action.mobile;

import java.util.List;

import javax.annotation.Resource;

import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;

import com.alpha.health.customer.model.Address;
import com.alpha.health.customer.model.Customer;
import com.alpha.health.customer.service.AddressService;
import com.alpha.health.customer.service.CustomerService;
import com.alpha.health.sys.action.BaseMobileLoginAction;

@Component
@Scope("prototype")
public class CustomerMobileAction extends BaseMobileLoginAction {
	private static final long serialVersionUID = 7176893045792402345L;

	private String uid;
	private Customer bean;
	private CustomerService customerService;
	
	@Resource private AddressService addressService;
	
	/**
	 * 获取地址列表
	 * 
	 * kora
	 *  
	 * */
	public void getAddress ()
	{
		System.out.println("===========================获取地址列表===========================");
		List<Address> list = addressService.findByAll();
		System.out.println(list.size());
		ajaxJsonSuccessMessageData("成功获取数据",addressService.findByAll());
	}
	
	//个人中心显示
	public void showPerson(){
		if(uid!=null) {
			bean=customerService.get(uid);
		}
		ajaxDateJson(bean);
	}
	
	/**
	 * @return uid
	 */
	public String getUid() {
		return uid;
	}

	/**
	 * @param uid 要设置的 uid
	 */
	public void setUid(String uid) {
		this.uid = uid;
	}

	/**
	 * @return bean
	 */
	public Customer getBean() {
		return bean;
	}

	/**
	 * @param bean 要设置的 bean
	 */
	public void setBean(Customer bean) {
		this.bean = bean;
	}

}

```