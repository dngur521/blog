# 의사 코드

Algorithm avl_del(root, key)
***
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
***
---


