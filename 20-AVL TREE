class Node:
    def __init__(self, key):
        self.key = key
        self.left = None
        self.right = None
        self.height = 1

def insert(root, key):
    if root is None:
        return Node(key)
    elif key < root.key:
        root.left = insert(root.left, key)
    else:
        root.right = insert(root.right, key)
    root.height = 1 + max(getHeight(root.left), getHeight(root.right))
    balance(root)
    return root

def delete(root, key):
    if root is None:
        return None
    elif key < root.key:
        root.left = delete(root.left, key)
    elif key > root.key:
        root.right = delete(root.right, key)
    else:
        if root.left is None:
            return root.right
        elif root.right is None:
            return root.left
        else:
            temp = findMin(root.right)
            root.key = temp.key
            root.right = delete(root.right, temp.key)
    root.height = 1 + max(getHeight(root.left), getHeight(root.right))
    balance(root)
    return root

def search(root, key):
    if root is None:
        return False
    elif key < root.key:
        return search(root.left, key)
    elif key > root.key:
        return search(root.right, key)
    else:
        return True

def getHeight(root):
    if root is None:
        return 0
    else:
        return root.height

def balance(root):
    balanceFactor = getHeight(root.left) - getHeight(root.right)
    if balanceFactor > 1:
        if getHeight(root.left.left) >= getHeight(root.left.right):
            root = rightRotate(root)
        else:
            root = leftRightRotate(root)
    elif balanceFactor < -1:
        if getHeight(root.right.right) >= getHeight(root.right.left):
            root = leftRotate(root)
        else:
            root = rightLeftRotate(root)
    return root

def rightRotate(root):
    newRoot = root.left
    root.left = newRoot.right
    newRoot.right = root
    root.height = 1 + max(getHeight(root.left), getHeight(root.right))
    newRoot.height = 1 + max(getHeight(newRoot.left), getHeight(newRoot.right))
    return newRoot

def leftRotate(root):
    newRoot = root.right
    root.right = newRoot.left
    newRoot.left = root
    root.height = 1 + max(getHeight(root.left), getHeight(root.right))
    newRoot.height = 1 + max(getHeight(newRoot.left), getHeight(newRoot.right))
    return newRoot

def leftRightRotate(root):
    root.left = leftRotate(root.left)
    return rightRotate(root)

def rightLeftRotate(root):
    root.right = rightRotate(root.right)
    return leftRotate(root)

def findMin(root):
    if root is None:
        return None
    elif root.left is None:
        return root
    else:
        return findMin(root.left)

def main():
    root = None
    root = insert(root, 10)
    root = insert(root, 20)
    root = insert(root, 30)
    root = insert(root, 40)
    root = insert(root, 50)

    print("Search for 30:", search(root, 30))
    print("Search for 60:", search(root, 60))

    root = delete(root, 30)
    print("Search for 30:", search(root, 30))

if __name__ == "__main__":
    main()
