# algorithm
def findTriplets(nums, n, Sum):
    i = 0
    j = 0
    k = 0
 
    # list to store all unique triplets.
    triplet = []
 
    # list to store already found triplets
    # to avoid duplication.
    uniqTriplets = []
 
    # Variable used to hold triplet
    # converted to string form.
    temp = ""
 
    # Variable used to store current
    # triplet which is stored in vector
    # if it is unique.
    newTriplet = [0, 0, 0]
 
    # Sort the input array.
    nums.sort()
 
    # Iterate over the array from the
    # start and consider it as the
    # first element.
    for i in range(n - 2):
         
        # index of the first element in
        # the remaining elements.
        j = i + 1
 
        # index of the last element.
        k = n - 1
 
        while(j < k):
           
            # If sum of triplet is equal to
            # given value, then check if
            # this triplet is unique or not.
            # To check uniqueness, convert
            # triplet to string form and
            # then check if this string is
            # present in set or not. If
            # triplet is unique, then store
            # it in list.
            if(nums[i] + nums[j] + nums[k] == Sum):
                temp = str(nums[i]) + ":" + str(nums[j]) + ":" + str(nums[k])
                if temp not in uniqTriplets:
                    uniqTriplets.append(temp)
                    newTriplet[0] = nums[i]
                    newTriplet[1] = nums[j]
                    newTriplet[2] = nums[k]
                    triplet.append(newTriplet)
                    newTriplet = [0, 0, 0]
 
                # Increment the first index
                # and decrement the last
                # index of remaining elements.
                j += 1
                k -= 1
                 
            # If sum is greater than given
            # value then to reduce sum
            # decrement the last index.
            elif(nums[i] + nums[j] + nums[k] > Sum):
                k -= 1
                 
            # If sum is less than given value
            # then to increase sum increment
            # the first index of remaining
            # elements.
            else:
                j += 1
 
    # If no unique triplet is found, then
       # return 0.
    if(len(triplet) == 0):
        return 0
     
    # Print all unique triplets stored in
    # list.
    for i in range(len(triplet)):
        print(triplet[i], end = ", ")
    return 1
 
# Driver Code
nums = [12, 3, 6, 1, 6, 9]
n = len(nums)
Sum = 24
 
# Function call
if(not findTriplets(nums, n, Sum)):
    print("No triplets can be formed.")
