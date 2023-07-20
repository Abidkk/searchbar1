# searchbar1



// components/SearchBar.js
import { useState } from 'react';
import { useRouter } from 'next/navigation'

const SearchBar = () => {
  const [searchQuery, setSearchQuery] = useState('');
  const router = useRouter();

  const handleSubmit = (e) => {
    e.preventDefault();

    const lowerCaseQuery = searchQuery.toLowerCase(); // Convert search query to lowercase

    if (lowerCaseQuery.includes('female') || lowerCaseQuery.includes('girl') ) {
      router.push('/female');
    } else if (lowerCaseQuery.includes('male') || lowerCaseQuery.includes('boy')){
    router.push('/male');
    }else if (lowerCaseQuery.includes('kid') || lowerCaseQuery.includes('bab')){
    router.push('/kids') 
    } else  {
        router.push('/allproducts')
    }
  };

  return (
    <form onSubmit={handleSubmit} 
    className='m-20 bg-red-100 cursor-pointer hover:border-red-400'
    > 
      <input
        type="text"
        value={searchQuery}
        onChange={(e) => setSearchQuery(e.target.value)}
        className='border-black border-2 px-5 mx-5'
      />
      <button type="submit"
       className='bg-sky-400 hover:bg-sky-800 duration-500 px-3 py-1 rounded-md'
       >Search</button>
    </form>

  );
};

export default SearchBar;
