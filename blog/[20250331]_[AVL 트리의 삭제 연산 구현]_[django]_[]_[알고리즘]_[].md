# 의사 코드


```C
Algorithm avl_del(root, key)

만약 노드가 본인 하나밖에 없으면 return;

// 삭제할 key에 해당하는 노드 찾는 과정
삭제할 key가 root의 값보다 작으면 {
  root의 왼쪽 자식이 존재하면 {
      root의 왼쪽 자식 = avl_del(root의 왼쪽 자식, key);
      // 왼쪽 자식노드에 대해서 삭제연산 수행(재귀호출)
   }
}

삭제할 key가 root의 값보다 크면 {
   root의 오른쪽 자식의 존재하면 {
      root의 오른쪽 자식 = avl_del(root의 오른쪽 자식, key);
      // 오른쪽 자식노드에 대해서 삭제연산 수행(재귀호출)
   }
}
// 삭제할 key에 해당하는 노드를 찾았을때 실행되는 과정
삭제할 root에 자식이 없는 경우 {
   root노드 메모리 해제;
   root = NULL;
   return NULL;
}

삭제할 노드에 자식이 1개만 있는 경우 {
   temp 노드 생성;
   root의 자식노드가 왼쪽에 있는 경우 {
      temp = root의 왼쪽 자식; }
   root의 자식노드가 오른쪽에 있는 경우 {
      temp = root의 오른쪽 자식; }
   root노드 메모리 해제;
   root = NULL;
   return NULL;
}

삭제할 노드에 자식이 2개 있는 경우 {
   temp 노드 생성;
   temp = root의 오른쪽 자식의 서브트리의 제일 값이 작은 노드;
   root를 temp의 위치로 이동;
   root의 오른쪽 자식이 존재하면 {
      root의 오른쪽 자식 = avl_del(root의 오른쪽 자식, temp의 값);
      // 이동한 노드의 오른쪽 자식에 대해서 삭제 연산 수행(재귀호출) }
}
return rebalance(root);
```
---

# 코드 구현

```C
// 삭제 연산에서 필요한 가장 작은 값을 갖는 노드를 찾는 함수
// 왼쪽 자식(자신보다 작은 값을 갖는 노드)이 없을때까지 계속 왼쪽으로 타고 내려가기
AVLNode* find_min(AVLNode* node) {
   while (node->left_child != NULL) {
   node = node->left_child; }
   return node;
}

// 삭제 연산을 수행하는 함수
AVLNode* avl_del(AVLNode** root, int key)
{
   // 만약 노드가 하나밖에 없으면 바로 반환
   if (*root == NULL) { return NULL; }

   // -----------삭제할 key에 해당하는 노드 찾는 과정 시작----------------
   // 만약 찾을 key가 현재 노드보다 작으면 왼쪽 자식노드로 이동
   if (key < (*root)->data) {
   if ((*root)->left_child) // NULL 체크 (왼쪽 자식노드에 값이 있는지 확인) {   
   // 왼쪽 자식노드에 대해서 삭제연산 수행(재귀호출)
         (*root)->left_child = avl_del(&((*root)->left_child), key); }
      }
   // 만약 찾을 key가 현재 노드보다 크면 오른쪽 자식노드로 이동
   else if (key > (*root)->data) {
   if ((*root)->right_child) { // NULL 체크 
   (오른쪽 자식노드에 값이 있는지 확인)
   // 오른쪽 자식노드에 대해서 삭제연산 수행(재귀호출)
   (*root)->right_child = avl_del(&((*root)->right_child), key); }
      }
      // ------------삭제할 key에 해당하는 노드 찾는 과정 끝-----------------

      // ----------key에 해당하는 node를 찾았을때 실행되는 과정 시작----------
   else {	
   // 삭제할 노드에 자식이 없는 경우 ( &&; and 연산 )
   if ((*root)->left_child == NULL && (*root)->right_child == NULL) {
   free(*root); *root = NULL; return NULL;
         // 바로 삭제할 노드 메모리 해제 후 반환
      }
   // 삭제할 노드에 자식이 1개만 있는 경우( ||; or 연산 )
   else if ((*root)->left_child == NULL || (*root)->right_child == NULL) {
   AVLNode* temp;
   // 삭제할 노드에 자식이 왼쪽or오른쪽에 있는지 찾아서 임시 노드에 대입
   if ((*root)->left_child != NULL) { // 자식노드가 왼쪽에 있는 경우
   temp = (*root)->left_child;
   }
         else { // 자식노드가 오른쪽에 있는 경우
            temp = (*root)->right_child;
         }
         free(*root); *root = NULL; return temp;
         // 삭제할 노드 메모리 해제 후 temp 노드 반환
   }

   // 삭제할 노드에 자식이 2개 있는 경우 
   //(자식이 없는경우도 아니고 1개만 있는 경우도 아닌 경우)
   else {
   AVLNode* temp = find_min((*root)->right_child); 
   // 오른쪽 자식의 서브트리 중에서 제일 작은 값의 노드 찾기
         (*root)->data = temp->data; 
   // 오른쪽 자식의 서브트리 중에서 제일 작은 값의 노드로 이동
         if ((*root)->right_child) { 
   // (이동한 노드의 오른쪽 자식이 존재하는지 확인)
         // 이동한 노드의 오른쪽 자식에 대해서 삭제 연산 수행(재귀호출)
            (*root)->right_child = avl_del(&((*root)->right_child), 
   temp->data);
         }
   }
   }
   // -----------key에 해당하는 node를 찾았을때 실행되는 과정 끝-----------
   // 최종적으로 삭제 이후 AVL트리의 균형이 깨질수도 있으니 리밸런스 수행 후 반환
   return rebalance(root);
}
// avl_search 함수 윗부분에 이 내용도 추가했다.
if (node == NULL) {
	// 찾는 key 값이 노드에 없을경우 print 추가
	printf("key %d not Found!\n", key);
	return NULL;}

```