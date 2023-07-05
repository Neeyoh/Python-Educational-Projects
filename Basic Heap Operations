# This question is designed to help you get a better understanding of basic heap operations.
# There are  types of query:
# "1" - Add an element  to the heap.
# "2" - Delete the element  from the heap.
# "3" - Print the minimum of all the elements in the heap.

# Enter your code here. Read input from STDIN. Print output to STDOUT
# Enter your code here. Read input from STDIN. Print output to STDOUT
class Heap:
    
    def __init__(self):
        self.items = []
        self.minimum = float('inf')  # Initialize minimum as positive infinity   
    
    def swap(self, indexOne, indexTwo):
        temp = self.items[indexOne]
        self.items[indexOne] = self.items[indexTwo]
        self.items[indexTwo] = temp
        
    def heapifyUp(self, index):
        while index > 0:
            parent_index = (index - 1) // 2
            
            if self.items[index] < self.items[parent_index]:
                self.swap(index, parent_index)
                # This next line just swaps the pointer from index which was moved up, to the parent_index spot 
                index = parent_index
            
            else:
                break
                
    def insert(self, item):
        self.items.append(item)
        if item < self.minimum: # Update minimum if necessary
            self.minimum = item
        # This next line chooses the last element (the newest added item) to heapifyUp
        self.heapifyUp(len(self.items) - 1)
        
    def heapifyDown(self, index):
        while True:
            left_child_index = 2 * index + 1
            right_child_index = 2 * index + 2
            smallest = index
            
            if (left_child_index < len(self.items) and self.items[left_child_index] < self.items[smallest]):
                smallest = left_child_index
            
            if (right_child_index < len(self.items) and self.items[right_child_index] < self.items[smallest]):
                smallest = right_child_index
                
            if smallest != index:
                self.swap(index, smallest)
                index = smallest
            else:
                break
                
    def delete(self, item):
        if item not in self.items:
            return None
        
        index = self.items.index(item)
        last_item = self.items.pop()
            
        if index < len(self.items):
            self.items[index] = last_item
            parent_index = (index - 1) // 2
                
            if index > 0 and self.items[index] < self.items[parent_index]:
                self.heapifyUp(index)
            else:
                self.heapifyDown(index)
                
        if item == self.minimum:
            self.minimum = min(self.items, default=float('inf'))
                    
        return item
        
    def print_minimum(self):
        return self.minimum

        
        
num_queries = int(input())    
heap = Heap()


for i in range(num_queries):
#        1 = insert
#        2 = delete
#        3 = print minimum
    query = input().split()
    a, b = query[0], query[1] if len(query) > 1 else None
    if a == '1':
        heap.insert(int(b))
    elif a == '2':
        heap.delete(int(b))
    elif a == '3':
        print(heap.print_minimum())