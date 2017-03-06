/**
 * 
 */
package edu.towson.cis.cosc442.project2.vendingmachine;

import static org.junit.Assert.*;

import org.junit.After;
import org.junit.Before;
import org.junit.Test;

/**
 * The unit test Class for VendingMachine.
 */
public class VendingMachineTest {
	/** Declaring necessary test objects */
	VendingMachineItem VendItem1;
	VendingMachineItem VendItem2; 
	String code1 = "A";
	String code2 = "1";
	Double amount1 = 1.75;
	Double amount2 = -1.25;
	VendingMachine vend;
	/**
	 * Initializes the necessary test objects for the test cases to use.
	 */
	@Before
	public void setUp() throws Exception {
		VendItem1 = new VendingMachineItem("Chips", .50);
		VendItem2 = new VendingMachineItem("Candy", 0);
		vend = new VendingMachine();
	}
	/**
	 * Test the AddItem method and its exception  
	 */
	@Test
	public void testAddItem() {
		vend.addItem(VendItem1, code1);
	}
	@Test (expected = Exception.class)
	public void testAddItemException() {
		vend.addItem(VendItem1, code1);
		vend.addItem(VendItem2, code1);
	}
	@Test (expected = Exception.class)
	public void testAddItemException2() {
		vend.addItem(VendItem1, code2);
	}
	/**
	 * Test the RemoveItem method  and its exception
	 */
	@Test
	public void testRemoveItem() {
		vend.addItem(VendItem1, code1);
		vend.removeItem(code1);
	}
	@Test (expected = Exception.class)
	public void testRemoveItemException() {
		vend.addItem(VendItem1, code1);
		vend.removeItem(code1);
		vend.removeItem(code1);
	}
	@Test (expected = Exception.class)
	public void testRemoveItemException2() {
		vend.addItem(VendItem1, code1);
		vend.removeItem(code2);
	}
	/**
	 * Test the InsertMoney method  and its exception
	 */
	@Test
	public void testInsertMoney() {
		vend.insertMoney(amount1);
	}
	@Test (expected = Exception.class)
	public void testInsertMoneyException() {
		vend.insertMoney(amount2);
	}
	/**
	 * Test the GetBalance method  
	 */
	@Test
	public void testGetBalance() {
		assertEquals(0, vend.getBalance(), 0.001);
		vend.insertMoney(amount1);
		assertEquals(amount1, vend.getBalance(), 0.001);
	}
	@Test (expected = Exception.class)
	public void testGetBalanceException() {
		vend.insertMoney(amount2);
	}
	/**
	 * Test the MakePurchase method  
	 */
	@Test
	public void testMakePurchase() {
		vend.insertMoney(amount1);
		vend.addItem(VendItem1, code1);
		assertTrue(vend.makePurchase(code1));				
	}
	@Test
	public void testMakePurchaseNoMoney() {
		vend.addItem(VendItem1, code1);
		assertFalse(vend.makePurchase(code1));
		assertFalse(vend.makePurchase("B"));
	}
	@Test
	public void testMakePurchaseWrongSlot() {
		assertFalse(vend.makePurchase("B"));
	}
	/**
	 * Test the ReturnCHange method  
	 */
	@Test
	public void testReturnChange() {
		vend.insertMoney(amount1);
		assertEquals(amount1, vend.returnChange(), 0.001);
	}
	@Test
	public void testReturnChangeAfterPurchase() {
		vend.insertMoney(amount1);
		vend.addItem(VendItem1, code1);
		vend.makePurchase(code1);
		assertEquals((amount1 - .50), vend.returnChange(), 0.001);
	}
	@Test(expected = Exception.class)
	public void testReturnChangeNegativeBalance() {
		vend.balance = -1.0;
		assertEquals((-1.0), vend.returnChange(), 0.001);
	}
	/**
	 * Cleans up test objects after a test case is executed.
	 */
	@After
	public void tearDown() throws Exception {
		VendItem1 = null;
		VendItem2 = null; 
		code1 = null;
		code2 = null;
		amount1 = null;
	    amount2 = null;
		vend = null;
	}

}
