### 红黑树左旋
    操作在旋转节点的右子树，将待旋转节点的右节点上升到父节点的位置上，同时
    将待旋转节点的左子树指给旋转节点的右树，待旋转节点的右子树的（根节点）升级
    到与旋转节点同级
    
    private void rotateLeft(RedBlackNode<T> node) {
        if (node != null) {
            RedBlackNode<T> rChild = node.right;
            node.right = rChild.left;
            if (rChild.left != null)
                rChild.left.parent = node;
            rChild.parent = node.parent;
            if (node.parent == null)
                root = rChild;
            else if (node.parent.left == node)
                node.parent.left = rChild;
            else
                node.parent.right = rChild;
            rChild.left = node;
            node.parent = rChild;
        }
    }
    
### 红黑树右旋
    操作在旋转节点的左子树，将待旋转节点的左节点上升到父节点的位置上，同时
    同时将待旋转节点右子树指给旋转节点的左树，待旋转节点左子树（根节点升级）
    到与旋转节点同级
    
    
    private void rotateRight(RedBlackNode<T> node) {
        if (node != null) {
            RedBlackNode<T> lChild = node.left;
            node.left = lChild.right;
            if (lChild.right != null)
                lChild.parent = node;
            lChild.parent = node.parent;
            if (node.parent == null)
                root = lChild;
            else if (node.parent.left == node)
                node.parent.left = lChild;
            else
                node.parent.right = lChild;
            lChild.right = node;
            node.parent = lChild;
        }
    }
