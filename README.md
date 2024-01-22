# votecontr
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SingerC {
    
    struct Singer {
        string name;
        uint256 votee;
    }

    
    Singer[] public sings;

    
    mapping(address => bool) public Voted;

    
    function addSin(string memory _name) public {
        sings.push(Singer(_name, 0));
    }

    
    function getSin() public view returns (uint256) {
        return sings.length;
    }

    
    function vote(uint256 _singerI) public {
        require(_singerI < sings.length, "Invalid ");
        require(Voted[msg.sender], " voted");

        sings[_singerI].votee++;
        Voted[msg.sender] = true;
    }

    function getVote(uint256 _singerIdx) public view returns (uint256) {
        require(_singerIdx < sings.length, "Invalid ");
        return sings[_singerIdx].votee;
    }
}
