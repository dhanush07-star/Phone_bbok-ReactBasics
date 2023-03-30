# Phone_bbok-ReactBasics



##############################/ useContext() /#################################

is there any way to pass value to the component without properties?
Ans: useContext() Hook 

all the child element which has been defined inside hasd the ability to get the values what the contect is exponsing!

recommanded to think of a data which is keep on flowing and the child componet who can listiend to that data using a function 

componets: Footer.js , SubscriberCountContext.js

explanation:

{SubscriberCountContext} is the pipeline created using React.createContect(),this is where the message going to flow;
        ^
        |
        |
        |
passes data to this 
context,so that child componts 
can listend to this pipline.




**Used in the project:

<SubscriberCountContext.Provider value={subscribersList.length}>
        <Footer></Footer>
</SubscriberCountContext.Provider>

@value={subscribersList.length}--> data we are pushing to SubscriberCountContext so that footer can 
listen to that message flow as its the child of SubscriberCountContext


in order footer to use the data
const  count= useContext(SubscriberCountContext);

####################################################################################

-------------------------------------------------------------------------------------


##################################/ useCallBack and useMemo /#############################
****ADVANCE HHOKS*******

useCallBack Hook:
        it will return memoized {function} based on dependencies

what is memoized?
        memoized the value of the function will never be executed again and again beoz the particular value 
        the return will always be the same

think of cache

***it will get the value and store***

useMemo Hook:
        it will return memoized {value} based on dependencies.


used in the project:
deleteSubscriberHandler

####################################################################################

-----------------------------------------------------------------------------------

##############################/ useReducer() /#################################

points:
1) Split state transformation witin componets to external methods.
2) Accepts a reducer function with componets intialState,
returns current component state, 
and propvides a dispatch function to update the state.
3) The state will be modified based on the dispatched information.

used in the project:

step 1)
  const [state, dispatchToTotalSubscriberReducer] = useReducer(
    TotalSubscribersReducer,
    { count: 0 }
  );

steo 2)
  dispatchToTotalSubscriberReducer: action ---> TotalSubscribersReducer

      dispatchToTotalSubscriberReducer({
      type: "UPDATE_COUNT",
      payload: data.length,
    });


step 3:
export function TotalSubscribersReducer(state,action){
    switch(action.type){
        case "UPDATE_COUNT":
            const updatedCount = action.payload;
            return {...state,count:updatedCount};
        default:
            return state;


    }}
