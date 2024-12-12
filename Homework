#include <iostream>
#include <memory>
using namespace std;

template <typename T>
class Tree {
private:
    struct Node {
        T key;
        unique_ptr<Node> left;
        unique_ptr<Node> right;

        Node(T k) : key(k), left(nullptr), right(nullptr) {}
    };

    unique_ptr<Node> root;

    ~Tree() = default;

    Tree(const Tree& other) {
        root = copyTree(other.root);
    }

    Tree& operator=(const Tree& other) {
        if (this == &other) return *this;
        root = copyTree(other.root);
        return *this;
    }

    void insert(T key) {
        auto newNode = make_unique<Node>(key);
        if (!root) {
            root = move(newNode);
        }
        else {
            Node* current = root.get();
            while (true) {
                if (key < current->key) {
                    if (!current->left) {
                        current->left = move(newNode);
                        break;
                    }
                    current = current->left.get();
                }
                else {
                    if (!current->right) {
                        current->right = move(newNode);
                        break;
                    }
                    current = current->right.get();
                }
            }
        }
    }

    void erase(T key) {
        root = eraseNode(move(root), key);
    }

    void print() const {
        printNode(root.get());
        cout << endl;
    }

private:
    void printNode(const Node* node) const {
        if (!node) return;
        printNode(node->left.get());
        cout << node->key << " ";
        printNode(node->right.get());
    }
};

    tree.erase(3);
    cout << "Tree after erasing 3: ";
    tree.print();

    return 0;
}
