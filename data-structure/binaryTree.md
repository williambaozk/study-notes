## 节点的数据结构类

```java
public class Node {
	public int data;
	public Node left;
	public Node right;
}
```
## 创建二叉树
```java
	/**
	 * 创建根节点
	 * @return
	 */
	public static Node createRoot() {
		Node root=new Node();
		System.out.println("请输入根节点：");
		root.data=new Scanner(System.in).nextInt();
		System.out.println("根节点创建成功!");
		return root;
		}
	//构建二叉树
	public static Node insert(Node root) throws Exception{
		while(true) {
			//获取待插入节点数据
			System.out.println("请输入待插入的节点");
			Node node=new Node();
			node.data=new Scanner(System.in).nextInt();
			
			//获取父节点数据
			System.out.println("请输入它的父节点：");
			int parentNodeData=new Scanner(System.in).nextInt();
			
			//获取插入方向
			System.out.println("请输入要插入到父节点的：1 左侧，2 右侧");
			int direction=new Scanner(System.in).nextInt();
			
			//插入节点
			root=insertNode(root,node,parentNodeData,direction);
			
			if(root==null) {
				System.out.println("未找到父节点，请重新输入！");
				continue;
			}
			System.out.println("插入成功!是否继续？1继续 2退出");
			if(new Scanner(System.in).nextInt()==1){
				continue;
			}else {
				break;
			}
		}
		return root;
	}
	
	//查找父节点并插入
	public static Node insertNode(Node root,Node node,int parentNodeData,int direction) throws Exception{
		if(root==null) {
			return null;
		}
		
		//找到父节点
		if(root.data==parentNodeData) {
			switch(direction) {
			case 1:
				if(root.left!=null) {
					throw new Exception("左节点已存在，不能插入！");
				}else {
					root.left=node;
				}
				break;
			case 2:
				if(root.right!=null) {
					throw new Exception("有节点已存在，不能插入！");
				}else {
					root.right=node;
				}
				break;
			}
		}else {
			insertNode(root.left,node,parentNodeData,direction);
			insertNode(root.right,node,parentNodeData,direction);
		}
		return root;
	}
  ```
  ## 查找节点
  ```java
  //查找节点
	public static boolean getNode(Node root,int data) {
		if(root==null) {
			return false;
		}
		if(root.data==data) {
			return true;
		}
		boolean result1=getNode(root.left,data);
		boolean result2=getNode(root.right,data);
		return result1||result2;
	}
  ```
  ## 二叉树深度
  ```java
  //获取二叉树的深度
	public static int getLength(Node root) {
		if(root==null) {
			return 0;
		}
		int leftLength,rightLength;
		leftLength=getLength(root.left);
		rightLength=getLength(root.right);
		if(leftLength>rightLength) {
			return leftLength+1;
		}else {
			return rightLength+1;
		}
	}
  ```
  ## 遍历二叉树
  ```java
  //先序遍历
	public static void preOrderTraverse(Node root) {
		if(root==null) {
			return;
		}
		System.out.print(root.data+" ");
		preOrderTraverse(root.left);//遍历左子树
		preOrderTraverse(root.right);//遍历右子树
	}
	//中序遍历
	public static void inOrderTraverse(Node root) {
		if(root==null) {
			return;
		}
		inOrderTraverse(root.left);
		System.out.print(root.data+" ");
		inOrderTraverse(root.right);
	}
	
	//后序遍历
	public static void postOrderTraverse(Node root) {
		if(root==null) {
			return;
		}
		postOrderTraverse(root.left);
		postOrderTraverse(root.right);
		System.out.print(root.data+" ");
	}
	//按层遍历
	public static void levelTraverse(Node root) {
		if(root==null) {
			return;
		}
		Queue<Node> queueNode=new LinkedList<Node>();
		queueNode.add(root);
		while(queueNode.size()!=0) {
			int length=queueNode.size();
			for(int i=0;i<length;i++) {
				Node temp=queueNode.poll();
				System.out.print(temp.data+" ");
				if(temp.left!=null) queueNode.add(temp.left);
				if(temp.right!=null) queueNode.add(temp.right);
			}
		}
	}
  ```
